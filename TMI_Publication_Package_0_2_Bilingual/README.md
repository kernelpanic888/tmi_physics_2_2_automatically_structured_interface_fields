# TMI Publication Package 0.2 — Bilingual Release

Author: **Salkutsan Aleksey**  
Version: **0.2 bilingual**  
Date: **2026-05-06**

This package contains the bilingual publication set for the Theory of Manifold Interfaces (TMI):

\[
\text{TMI Core 0.2}\Rightarrow\text{TMI-Physics 2.2}\Rightarrow\text{Computational Validation Tests 1--11}
\]

## Contents

```text
01_TMI_Core_0_2_Automatic_Interfaces/
  RU/   Russian PDF and TeX
  EN/   English PDF and TeX
  PDF/  PDF copies
  TEX/  TeX copies

02_TMI_Physics_2_2_Automatically_Structured_Interface_Fields/
  RU/   Russian PDF and TeX
  EN/   English PDF and TeX
  PDF/  PDF copies
  TEX/  TeX copies

03_Computational_Validation_Tests_1_11/
  report/       Russian and English report PDFs/TeX plus full report packages
  report_EN/    English report with figures, data, and test archives
  tests_archives/  Archives of Tests 1--11

04_Source_Notes/
  Source notes used during development.

05_Release_Metadata/
  Manifest, release notes, and checksums.
```

## English documents added in this release

1. `tmi_core_0_2_automatic_interfaces_en.pdf`
2. `tmi_physics_2_2_automatically_structured_interface_fields_en.pdf`
3. `tmi_computational_validation_report_v2_en.pdf`

## Scientific status

This package separates three levels:

1. **TMI Core 0.2** — axiomatic and conceptual core.
2. **TMI-Physics 2.2** — physical module based on automatically structured interface fields.
3. **Computational Validation Tests 1--11** — numerical support for an engineering projection of adaptive interface control.

The computational report does **not** claim a laboratory proof of the physical field \(\Xi_I^{auto}\). It reports reproducible numerical validation, robustness checks, failure-boundary analysis, adversarial failure, and safety-aware recovery.

Key computational conclusions:

\[
I_Q^{coh-auto}\Rightarrow T_2^{eff}\uparrow\Rightarrow P_{success}\uparrow
\]

but also:

\[
AutoInterface\not\Rightarrow SafeInterface
\]

and:

\[
AutoInterface+SafetyLayer\Rightarrow SaferAdaptiveControl.
\]
