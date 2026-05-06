# TMI Computational Test 21: Cost-Interface Boundary Test

## Purpose

Test 20 showed that performance and cost must be evaluated together.
Test 21 explicitly finds the switching boundary between high-performance and
cost-aware control.

## Core equations

Utility:

`U = DeltaP - lambda * ExtraCost`

Boundary between high-performance and cost-aware control:

`U_high_perf = U_cost_aware`

Critical cost weight:

`lambda* = (DeltaP_high_perf - DeltaP_cost_aware) / (ExtraCost_high_perf - ExtraCost_cost_aware)`

If:

`lambda < lambda*`

then high-performance control is preferred.

If:

`lambda > lambda*`

then cost-aware control is preferred.

## Main boundary found

| Boundary | Mean lambda* | Median lambda* | 95% low | 95% high |
|---|---:|---:|---:|---:|
| high_perf_online = cost_aware_low | 0.063608 | 0.064021 | 0.024043 | 0.112104 |

## Hardware multiplier boundary

For fixed lambda, the critical hardware cost multiplier is:

`k* = lambda* / lambda`

| lambda | mean k* | median k* | 95% low | 95% high |
|---:|---:|---:|---:|---:|
| 0.010 | 6.361 | 6.402 | 2.404 | 11.210 |
| 0.020 | 3.180 | 3.201 | 1.202 | 5.605 |
| 0.035 | 1.817 | 1.829 | 0.687 | 3.203 |
| 0.050 | 1.272 | 1.280 | 0.481 | 2.242 |
| 0.070 | 0.909 | 0.915 | 0.343 | 1.601 |

## Phase-grid result

| Quantity | Value |
|---|---:|
| Lambda grid values | 57 |
| Hardware cost multipliers | 50 |
| Grid cells | 2850 |
| High-performance best cells | 404 |
| Cost-aware low best cells | 2446 |
| Latency optimized best cells | 0 |

## TMI interpretation

The boundary is not merely a line. It becomes an interface when it triggers
a transition of control regimes:

`I_cost := B_cost ∘ T(Control_high_perf <-> Control_cost_aware)`

where:

`B_cost : U_high_perf = U_cost_aware`

## Key conclusion

The cost-interface boundary exists. Below it, high-performance control is justified.
Above it, cost-aware control becomes the better regime.

## Scientific caution

This is an analytical/computational boundary test based on the Test 20 synthetic cost
model. The next step is to replace synthetic costs with hardware-specific cost estimates.
