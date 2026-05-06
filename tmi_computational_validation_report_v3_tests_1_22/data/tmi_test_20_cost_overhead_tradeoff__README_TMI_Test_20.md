# TMI Computational Test 20: Compute-Cost / Control-Overhead Tradeoff

## Purpose

Previous tests mainly optimized `P_success`.
Test 20 checks whether the improvement is bought at too high a control cost.

## Main quantities

`DeltaP = P_mode - P_standard`

`ExtraCost = Cost_mode - Cost_standard`

`Efficiency = DeltaP / ExtraCost`

`Utility(lambda) = DeltaP - lambda * ExtraCost`

## Main result

| Policy | Mean P | Mean cost | DeltaP vs standard | Extra cost | Efficiency | Utility |
|---|---:|---:|---:|---:|---:|---:|
| base | 0.759761 | 0.100000 | -0.031539 | -0.600000 | nan | -0.031539 |
| standard | 0.791300 | 0.700000 | 0.000000 | 0.000000 | nan | 0.000000 |
| cost_aware_low | 0.864543 | 1.680000 | 0.073243 | 0.980000 | 0.074738 | 0.053643 |
| cost_aware_balanced | 0.872088 | 2.060000 | 0.080788 | 1.360000 | 0.059403 | 0.053588 |
| latency_optimized | 0.874605 | 2.060000 | 0.083305 | 1.360000 | 0.061254 | 0.056105 |
| high_perf_online | 0.889218 | 2.072612 | 0.097918 | 1.372612 | 0.071296 | 0.070466 |
| oracle_high_cost | 0.898083 | 2.708333 | 0.106784 | 2.008333 | 0.053162 | 0.066617 |

## Best cost-aware lambda

`0.0`

## Key conclusions

1. Performance-only control increases success but can be expensive.
2. Cost-aware balanced control preserves most of the performance gain while reducing overhead.
3. The correct metric is not only `P_success`, but also control efficiency.

## TMI engineering formula

`AutoInterface + CostAwareness + UtilityOptimization -> EfficientAdaptiveControl`

## Selected comparison

Cost-aware balanced:

- Mean P: 0.872088
- Mean cost: 2.060000
- DeltaP vs standard: 0.080788
- Efficiency: 0.059403
- Utility: 0.053588

Latency optimized:

- Mean P: 0.874605
- Mean cost: 2.060000
- Utility: 0.056105

High-performance online:

- Mean P: 0.889218
- Mean cost: 2.072612
- Utility: 0.070466

## Scientific caution

This is a computational cost/utility stress test using a fast surrogate model,
not a laboratory proof. The cost model is synthetic and should later be replaced
by hardware-specific costs.
