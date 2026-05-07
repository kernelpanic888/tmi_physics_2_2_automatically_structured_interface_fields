# Publication Boundary

This repository contains the public publication layer of TMI-Physics 2.2.

## Public layer

The following materials may be included in public releases:

- theoretical formulas and high-level methodology;
- public summaries of computational tests;
- aggregated validation results;
- cautious scientific conclusions;
- public-safe figures and tables;
- limitations and negative results;
- general statements that QPU behavior is backend-dependent and calibration-state-dependent.

## Private layer

The following materials must not be included in public releases:

- full QPU test scripts;
- backend profiling code;
- selector logic;
- thresholds;
- optimizer internals;
- calibration-state mapping;
- raw backend diagnostic CSV files;
- private QPU archives;
- production report generator logic;
- hardware-aware scoring details;
- full implementation of Tests 29–35.

## Public-safe wording

Cloud-QPU tests indicate that hardware-aware TMI behavior is backend-dependent and calibration-state-dependent. Positive advantage was observed under some QPU conditions, but it was not stable across all confirmation runs. Time-resolved backend profiling is therefore required before claiming stable QPU advantage.

## Current QPU status

Tests 29–34 are private technical validation artifacts. Only summary-level results may be used in publications.

## Rule

Before publishing any new file, ask:

Is this a scientific summary or an implementation detail?

If it is a scientific summary, it may be public.
If it is implementation logic, calibration logic, backend profiling, selector logic, or raw QPU data, it must remain private.
