# TMI Computational Test 14: Noise-Model Stress Test

## Purpose

Test 14 checks whether the adaptive-interface advantage persists across different noise models:

1. `pure_dephasing`
2. `depolarizing`
3. `amplitude_damping`
4. `mixed`

The test uses an independent compact density-matrix simulator with local Kraus-style channels.

## Main criterion

`mean(P_TMI - P_standard) > 0`

and:

`Pr(P_TMI > P_standard) > 0.5`

## Overall results

| Metric | Value |
|---|---:|
| Total runs | 216 |
| Noise models | 4 |
| Circuit families | 3 |
| Mean P_base | 0.878771 |
| Mean P_standard | 0.913466 |
| Mean P_TMI | 0.920233 |
| Mean delta TMI - standard | 0.006767 |
| 95% CI delta | [0.005375, 0.008263] |
| Pr(TMI > standard) | 0.666667 |
| Noise models passed | 3 / 4 |
| Circuit/noise cells passed | 9 / 12 |

## Results by noise model

| Noise model | Mean base | Mean standard | Mean TMI | Mean delta | Pr(TMI > standard) | Passed circuits |
|---|---:|---:|---:|---:|---:|---:|
| amplitude_damping | 0.931692 | 0.933125 | 0.932808 | -0.000317 | 0.203704 | 0/3 |
| depolarizing | 0.887828 | 0.918781 | 0.923825 | 0.005044 | 0.777778 | 3/3 |
| mixed | 0.876958 | 0.910794 | 0.918300 | 0.007506 | 0.796296 | 3/3 |
| pure_dephasing | 0.818604 | 0.891164 | 0.905997 | 0.014833 | 0.888889 | 3/3 |

## Interpretation

If the TMI advantage persists across dephasing, depolarizing, amplitude damping and mixed noise, then the mechanism is less likely to be tied to one narrow noise model.

Amplitude damping is expected to be the hardest case, because it is less controllable by phase/control adaptation than pure dephasing.

## Scientific caution

This is still computational validation, not a laboratory proof. It tests robustness of the adaptive-interface mechanism across noise assumptions.
