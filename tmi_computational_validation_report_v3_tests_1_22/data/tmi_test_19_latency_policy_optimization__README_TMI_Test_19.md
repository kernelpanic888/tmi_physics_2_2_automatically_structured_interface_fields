# TMI Computational Test 19: Latency-Aware Policy Optimization

## Purpose

Test 18 showed that latency-aware control was better than standard, but slightly
worse than raw delayed control. Test 19 optimizes the latency-aware policy.

## Main target

`P_latency_optimized > P_delayed_d2`

and:

`P_latency_optimized > P_delayed_d3`

while preserving:

`P_latency_optimized > P_standard`

## Method

The optimized policy uses a predictive distribution over current noise based on
stale classification history:

`NoiseClass(t - Δt) -> PredictiveNoiseDistribution(t) -> ControlLayer(t)`

Instead of a hard conservative fallback, it selects the control layer that maximizes
expected segment success under the predicted noise distribution, with a risk penalty.

## Best tuned parameters

| Parameter | Value |
|---|---:|
| risk_lambda | 0.000000 |
| smoothing_alpha | 0.450000 |
| delay | 2 |
| tuning objective | maximize optimized - delayed_d2 |

## Main results on held-out evaluation split

| Metric | Value |
|---|---:|
| Evaluation runs | 216 |
| Tuning runs | 216 |
| Current classifier accuracy | 0.807613 |
| Mean P_standard | 0.792817 |
| Mean P_delayed_d2 | 0.860673 |
| Mean P_delayed_d3 | 0.862640 |
| Mean P_latency_optimized | 0.875033 |
| Mean P_oracle | 0.892555 |
| Delta optimized - standard | 0.082217 |
| Delta optimized - delayed_d2 | 0.014360 |
| Delta optimized - delayed_d3 | 0.012393 |
| Delta optimized - oracle | -0.017521 |
| Pr(optimized > standard) | 1.000000 |
| Pr(optimized > delayed_d2) | 0.949074 |
| Pr(optimized > delayed_d3) | 0.925926 |

## Key conclusion

The optimized latency-aware policy improves over raw delayed feedback. This supports:

`AutoInterface + PredictiveLatencyModel + RiskAwareLayerSelection -> LatencyRobustControl`

## Scientific caution

This is a computational optimization test using a fast surrogate model, not a laboratory proof.
