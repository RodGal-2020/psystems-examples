# Results obtained debugging

| system | n_rules | read_rules | rule_types | notes |
|--------|---------|------------|------------|-------|
| RAPS_like_evolution | 27 | 14 | evolution, stochastic evolution | - |
| RAPS_like_evolution_stochastic | 13 | 13 | stochastic evolution | We get $\infty$ as `sc`, even if it was defined as 1 |
| RAPS_like_evolution_non_stochastic | 14 | 14 | non-stochastic evolution | - |
| conflict_01 | 2 | 1 | First minimal example | - |
| conflict_02 | 2 | 2 | First minimal example with different RHSs | - |
| conflict_03 | 2 | 2 | First minimal example with different LHSs | - |
| conflict_04 | 3 | 2 | One ev_rule, one sc_ev_rule and one rule with a random feature | Reads only the ev_rule and the one with the random feature |
