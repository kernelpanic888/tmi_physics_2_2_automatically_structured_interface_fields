# TMI Computational Test 15: Amplitude-Damping Recovery Test

## Purpose

Test 14 showed that amplitude damping is a weak/failure regime for a coherence-oriented TMI controller. Test 15 adds a relaxation-aware interface layer with a second control parameter `r`.

Main test:

`I_Q^coh-auto + RelaxationAwareLayer -> T1_eff increases -> P_success increases`

## Compared modes

1. `base`: no protection.
2. `standard`: fixed coherence-oriented protection.
3. `coh_TMI`: adaptive coherence controller, not relaxation-aware.
4. `relax_TMI`: adaptive coherence + relaxation-aware controller.

## Circuit families

- `excited_memory_111`
- `excited_entangle_inverse_111`
- `partial_excited_101`
- `ghz_excited_hold`

## Main results

| Metric | Value |
|---|---:|
| Total runs | 144 |
| Circuit families | 4 |
| Mean P_base | 0.197585 |
| Mean P_standard | 0.207660 |
| Mean P_coh_TMI | 0.207703 |
| Mean P_relax_TMI | 0.360882 |
| Mean delta coh_TMI - standard | 0.000043 |
| 95% CI coh delta | [-0.000379, 0.000481] |
| Pr(coh_TMI > standard) | 0.409722 |
| Mean delta relax_TMI - standard | 0.153222 |
| 95% CI relax delta | [0.143388, 0.163214] |
| Pr(relax_TMI > standard) | 1.000000 |
| Mean delta relax_TMI - coh_TMI | 0.153179 |
| Pr(relax_TMI > coh_TMI) | 1.000000 |
| Mean T1 standard | 60.111327 |
| Mean T1 relax_TMI | 117.237570 |
| Circuits relax passed vs standard | 4 / 4 |
| Circuits relax passed vs coh_TMI | 4 / 4 |

## Interpretation

A coherence-only interface is not sufficient for amplitude-damping dominated noise. A relaxation-aware layer can recover part of the lost advantage by learning a second control parameter that reduces effective amplitude damping at the cost of extra control error.

## Scientific caution

This is a fast computational surrogate, not a laboratory proof. It shows that the Test 14 amplitude-damping failure can be addressed inside the model by adding a recovery mechanism, but it does not prove that such a mechanism exists in physical hardware.
