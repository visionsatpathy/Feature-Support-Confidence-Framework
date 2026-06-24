# Feature-Support-Confidence-Framework
A physics-aware feature validation framework for hallucination analysis in biomedical images for diagnosis.
# Feature Support Validation (PSVS) for Hallucination Analysis

## Overview

This repository implements a physics-aware framework for **feature-level hallucination analysis** in computational imaging, called **Perturbation-based Signal Validation Strategy (PSVS)**.

The central question is:

> Is a reconstructed feature truly real, or was it introduced by the reconstruction pipeline?

A feature should not be trusted merely because it appears visually plausible.
It must be validated based on **measurement-supported existence**.

---

## What is Hallucination?

Hallucination is often confused with:

* uncertainty
* poor sensor resolution
* low SNR
* inverse ambiguity

These are **not hallucinations**.

In this framework, hallucination occurs when reconstruction:

* introduces a feature not strongly supported by acquired measurement, or
* suppresses a feature that was physically supported by the measured signal

---

## Feature Support Confidence (FSC)

This framework introduces a feature-specific parameter:

### Feature Support Confidence (FSC)

FSC quantifies how strongly a reconstructed feature is supported by acquired measurement.

This is **not AI model confidence**.

It measures **measurement consistency under feature perturbation**.

---

## PSVS Workflow

1. Perform reconstruction / enhancement
2. Identify suspicious feature
3. Remove selected feature from reconstructed image
4. Forward-model modified reconstruction into measurement space
5. Compare predicted measurement with acquired measurement

Interpretation:

* Significant mismatch → strong feature support
* Negligible change → hallucination candidate

---

## Included Implementations

### CLAHE-based PSVS

* `psvs_clahe_tester.p`
* `feature_score.p`

Validates hallucinations caused by contrast enhancement.

### Frangi-based PSVS

* `psvs_frangi_tester.p`
* `feature_score_frangi.p`

Validates hallucinations caused by vessel enhancement.

---

## Generalization to Other Reconstruction Methods

This framework is **not limited to CLAHE or Frangi**.

For any other reconstruction or enhancement pipeline:

1. Modify the code to perform your reconstruction first
2. Select and remove suspicious features
3. Replace the forward-modeling stage with the physics/model appropriate to your imaging system

This makes PSVS adaptable to:

* classical enhancement pipelines
* iterative reconstruction
* inverse solvers
* deep learning reconstruction models

---

## Requirements

* MATLAB
* Image Processing Toolbox

Code is provided as protected `.p` files for executable use while preserving source implementation.


---

## Author

**Sweta Satpathy**
Photonics • Computational Imaging • Physics-Aware Reconstruction

