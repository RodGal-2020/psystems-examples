# Stochastic models

## `stochastic_model.pli`

## `basic_stochastic_model.pli`
!evolution_rule
{
  [ u -> v ]'h;
}

!skeleton_rule
{
  [ [ ]'h ]'h1 --> [ [ ]'h ]'h2 @ sc(int_t);
}


# Stochastic systems

## `stochastic_1.pli`

@mu = [ [ [ ]'3 ]'1 [ ]'2 ]'0; <br>
[ [ ]'3 ]'1 --> [ [ ]'3 ]'2 @ sc=2;