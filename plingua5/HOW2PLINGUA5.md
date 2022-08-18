# Recordatorio Ubuntu en Windows
Habiendo abierto una terminal normal y corriente de Windows en la carpeta correspondiente, basta con recurrir a la orden `bash` para entrar en el modo Ubuntu. Nótese que no puedo emplear la orden `ubuntu`, pues eso me mandaría a una dimensión independiente en la que no puedo acceder a nada de lo que tengo en Windows. También existe la orden `Abrir shell de Linux aquí`, que hace exactamente lo que quiero.

# Arrancando con PLingua 5

## Instalación
Recurrir a la siguiente orden o bien a la vieja confiable, GitHub Desktop, y clonarlo manualmente recurriendo al enlace.
```
git clone https://github.com/RGNC/plingua.git
```

Una vez en la carpeta del repositorio se puede empezar a compilar con las siguientes órdenes:
```
make grammar
make compiler
make simulator
sudo make install
```

Tras esto `plingua` se reconocerá como un comando, pudiendo hacer de esta forma cosas como:

```
plingua prueba.pli -o prueba.json -f json
plingua prueba.pli -o prueba.xml -f xml

```

# *features*
Tal y como indica el nombre, las *features* son atributos adicionales que se pueden definir para incrementar la complejidad de nuestros modelos tanto como queramos. Si bien esto suele reducirse a la inclusión de una variable adicional en cada regla, en la práctica podemos hacer casi cualquier cosa.

## Definición de *features*
Recurriendo a @ podemos definir una nueva *feature* dentro de un modelo de PLingua 5. En el siguiente ejemplo se define una llamada `sc`, de *stocastic constant*, con el tipo de variable entre paréntesis, en este caso entera.
```
  [ [ ]'h ]'h1 --> [ [ ]'h ]'h2 @ sc(int_t);
```

## Uso de *features*
Definida la *feature* en el modelo para utilizarla procedemos como en el siguiente ejemplo:
```
@model<stochastic>
@include "stochastic_model.pli"

def main()
{
  @mu = [ [ [ ]'3 ]'1 [ ]'2 ]'0;
  [ [ ]'3 ]'1 --> [ [ ]'3 ]'2 @ sc=2;
}
```
Podemos ver aquí cómo le asignamos a nuestra *feature* `sc` un valor entero. 

## Lectura de *features*
Al generar un archivo JSON o XML es posible recuperar el valor de estas variables en la sección de *features* del mismo.

## Estructura de los XML generados
cereal > file
              > header $Properties
              > version $Properties
              > psystem
                        > objects $Properties
                        > labels $RAP (bound to structure)
                        > features (?)
                        > strings $Properties
                        > max_multiplicity $Properties
                        > model > id $Properties
                        > semantics $RAP
                        > structure $RAP (bound to labels)
                        > multisets $RAP
                        > rules > left_hand_rule, arrow, right_hand_rule $Rules
                        > features (again) $Properties

## RAPS' status
- [x] cereal > file
              - [-] > header $Properties
              - [x] > version $Properties
              - [ ] > psystem
                        - [x] > objects $Properties
                        - [x] > labels $RAP (bound to structure)
                        - [-] > features (?)
                        - [x] > strings $Properties
                        - [x] > max_multiplicity $Properties
                        - [x] > model > id $Properties
                        - [ ] > semantics $RAP
                        - [ ] > structure $RAP (bound to labels)
                        - [ ] > multisets $RAP
                        - [ ] > rules > left_hand_rule, arrow, right_hand_rule $Rules
                        - [ ] > features (again) $Properties
