# TMI Computational Test 16: Noise-Classifier Adaptive Interface

## Purpose

Test 14 showed that a coherence-oriented TMI layer works for several noise classes
but fails for amplitude damping. Test 15 showed that a relaxation-aware layer can
recover amplitude damping.

Test 16 checks whether the interface can first classify the dominant noise type and
then choose the appropriate control layer.

## Noise classes

- dephasing
- depolarizing
- amplitude_damping
- mixed

## Control layers

- dephasing -> coherence layer
- depolarizing -> depolarizing/gate-error layer
- amplitude_damping -> relaxation-aware layer
- mixed -> mixed control layer

## Main chain

`NoiseFeatures -> NoiseClass -> ControlLayer -> P_success increase`

## Overall results

| Metric | Value |
|---|---:|
| Total runs | 480 |
| Noise classes | 4 |
| Circuit families | 4 |
| Classification accuracy | 0.952083 |
| Mean P_base | 0.604519 |
| Mean P_standard | 0.634632 |
| Mean P_coherence_only | 0.650651 |
| Mean P_oracle | 0.690348 |
| Mean P_classifier_TMI | 0.690026 |
| Mean delta classifier - standard | 0.055394 |
| 95% CI delta classifier - standard | [0.053064, 0.057607] |
| Pr(classifier > standard) | 1.000000 |
| Mean delta classifier - coherence-only | 0.039375 |
| Overall status | passed |

## Results by noise class

| Noise class | Accuracy | Standard | Coh-only | Classifier TMI | Delta vs standard | Status |
|---|---:|---:|---:|---:|---:|---|
| amplitude_damping | 1.000000 | 0.594953 | 0.590944 | 0.687597 | 0.092644 | passed |
| dephasing | 1.000000 | 0.689098 | 0.737100 | 0.737100 | 0.048001 | passed |
| depolarizing | 1.000000 | 0.674774 | 0.676925 | 0.708805 | 0.034030 | passed |
| mixed | 0.808333 | 0.579703 | 0.597636 | 0.626602 | 0.046899 | passed |

## Interpretation

The classifier interface tests a more explicitly manifold-style control principle:

`AutoInterface + NoiseClassification + SpecializedControlLayer -> AdaptiveControl`

The goal is not that one universal control law solves all noise. The goal is that the
interface can choose the appropriate layer for the detected noise regime.

## Scientific caution

This is a fast computational surrogate test, not a laboratory proof.
Its role is to test whether noise-specific adaptive interface selection is a viable
engineering projection of the TMI quantum-control idea.
