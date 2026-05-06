# TMI Computational Test 17: Online Noise-Drift Adaptation

## Purpose

Test 16 used a noise classifier for fixed noise classes. Test 17 introduces noise drift:
the noise type changes during the computation. The adaptive interface must re-classify
online and switch its control layer.

## Main chain

`NoiseFeatures -> NoiseClass -> ControlLayer -> P_success increases`

## Compared modes

1. `standard`: fixed standard protection.
2. `coherence_only`: coherence-oriented TMI layer only.
3. `static_classifier`: classifies the initial noise and never updates.
4. `online_classifier`: re-classifies after noise changes and switches control layer.
5. `oracle`: knows the true current noise class.

## Results

| Metric | Value |
|---|---:|
| Total runs | 480 |
| Drift sequences | 5 |
| Circuit families | 4 |
| Mean P_standard | 0.521166 |
| Mean P_static_classifier | 0.528848 |
| Mean P_online_classifier | 0.546651 |
| Mean P_oracle | 0.552026 |
| Delta online - standard | 0.025485 |
| 95% CI online - standard | [0.024367, 0.026598] |
| Delta online - static | 0.017803 |
| 95% CI online - static | [0.016710, 0.018860] |
| Delta online - oracle | -0.005375 |
| Online classification accuracy | 0.815755 |
| Static classification accuracy | 0.299479 |
| Overall status | passed |

## Interpretation

If online classification beats both standard protection and static classification,
then the interface is not merely noise-specific; it is drift-adaptive.

## Scientific caution

This is a fast computational stress test. It does not prove that an automatically
structured interface field exists in nature. It tests an engineering projection:
an adaptive interface can track changing noise classes and switch control layers.
