# TMI Computational Test 13: Independent Simulator Implementation

## Purpose

Test 13 checks whether the adaptive-interface advantage survives an implementation
that is independent from Tests 7--8.

This simulator uses:

1. Qiskit/Cirq-style declarative circuit descriptions;
2. local Kraus-style dephasing and depolarizing channels;
3. a separate adaptive controller based on grid refinement, conservative memory and fallback;
4. a standalone pass/fail criterion.

## Main criterion

`mean(P_TMI - P_standard) > 0`

and:

`Pr(P_TMI > P_standard) > 0.60`

and:

`95% bootstrap CI lower bound for mean delta > 0`

## Overall result

| Metric | Value |
|---|---:|
| Circuit families | 4 |
| Total environments | 72 |
| Mean P_base | 0.356210 |
| Mean P_standard | 0.432094 |
| Mean P_TMI | 0.544228 |
| Mean delta TMI - standard | 0.112134 |
| 95% CI delta low | 0.096255 |
| 95% CI delta high | 0.128160 |
| Pr(TMI > standard) | 1.000000 |
| Circuits passed | 4 / 4 |
| Overall passed | True |

## Results by circuit

| Circuit | Base | Standard | TMI | Delta | Pr(TMI > standard) | Passed |
|---|---:|---:|---:|---:|---:|---:|
| sdk_style_balanced_inverse | 0.260144 | 0.384268 | 0.555647 | 0.171378 | 1.000000 | True |
| sdk_style_deep_mixed_inverse | 0.370272 | 0.433888 | 0.509388 | 0.075500 | 1.000000 | True |
| sdk_style_ghz_echo | 0.505545 | 0.541575 | 0.617816 | 0.076241 | 1.000000 | True |
| sdk_style_phase_chain | 0.288881 | 0.368646 | 0.494062 | 0.125417 | 1.000000 | True |

## Interpretation

A positive result means that the computational advantage is less likely to be an artifact
of the original simulator architecture.

## Scientific caution

This is still a computational validation on toy quantum circuits. It is not a laboratory proof.
Its purpose is to test implementation independence.
