# TMI Computational Test 22: Multi-Objective Interface Control

## Purpose

Test 21 found a single cost-interface boundary.
Test 22 generalizes this to a multi-objective boundary manifold.

Instead of optimizing only:

`P_success`

or:

`Utility = DeltaP - lambda * Cost`

we optimize a vector:

`O(policy) = (P_success, Cost, Safety, Latency, Robustness)`

The score for a preference vector `w` is:

`Score(policy; w) = w · O(policy)`

A boundary occurs where two policies tie:

`Score_i(w) = Score_j(w)`

The union of these switching surfaces approximates:

`M_boundary`

## Objectives

1. Performance: `P_success`
2. Cost: low control overhead
3. Safety: avoidance of unsafe/aggressive control
4. Latency: low response delay
5. Robustness: stability under sequence complexity

## Policy objective vectors

| Policy | P score | Cost score | Safety | Latency score | Robustness | Pareto |
|---|---:|---:|---:|---:|---:|---:|
| cost_aware_balanced | 0.677242 | 0.352381 | 0.829724 | 0.352512 | 0.811063 | True |
| cost_aware_low | 0.645683 | 0.533333 | 0.887500 | 0.589486 | 0.841033 | True |
| high_perf_online | 0.748892 | 0.346375 | 0.632359 | 0.255227 | 0.691897 | True |
| latency_optimized | 0.687771 | 0.352381 | 0.764184 | 0.463684 | 0.844863 | True |
| oracle_high_cost | 0.785974 | 0.043651 | 0.593077 | 0.030640 | 0.836288 | True |
| standard | 0.339326 | 1.000000 | 0.773894 | 0.875784 | 0.712153 | True |

## Winner share in sampled preference space

| Policy | Share |
|---|---:|
| cost_aware_balanced | 0.000000 |
| cost_aware_low | 0.373083 |
| high_perf_online | 0.004375 |
| latency_optimized | 0.002167 |
| oracle_high_cost | 0.012625 |
| standard | 0.607750 |

## Named preference profiles

| Profile | Best policy | Best score |
|---|---|---:|
| performance_first | cost_aware_low | 0.679823 |
| cost_first | standard | 0.821431 |
| safety_first | cost_aware_low | 0.764043 |
| latency_first | standard | 0.761476 |
| robustness_first | cost_aware_low | 0.751226 |
| balanced | standard | 0.711316 |
| safety_cost_balanced | standard | 0.773740 |
| latency_robust | standard | 0.744775 |

## TMI interpretation

A single cost boundary:

`B_cost : U_high_perf = U_cost_aware`

is generalized to a multi-objective boundary manifold:

`M_boundary = { w : argmax_policy Score(policy; w) changes }`

When the system uses this manifold to switch regimes, it becomes a manifold interface:

`I_multi := M_boundary ∘ T(Control_i <-> Control_j)`

## Main conclusion

The optimal interface control regime depends on the preference vector.
There is no single universally best policy across all objectives.

This supports:

`AutoInterface + MultiObjectivePreference + BoundaryManifoldDetection -> ManifoldAdaptiveControl`

## Scientific caution

The non-performance metrics Safety, Latency and Robustness are structured modeling
assumptions derived from the Test 20 environment. They are not hardware measurements.
Future tests should replace them with hardware-specific values.
