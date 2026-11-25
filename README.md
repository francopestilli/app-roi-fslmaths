[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.444-blue.svg)](https://doi.org/10.25663/bl.app.444)

# app-roi-fslmaths

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Combines one ROI from each of two ROI sets with FSL fslmaths (add, subtract, multiply, divide or mask), for example to remove a lesion from a region of interest.**

Copies the named ROI from each input ROI directory and runs fslmaths <roi_1> -<function> <roi_2>, writing the result as a new ROI; with sub the result is clipped to 0-1 so it stays binary. Use it to mask an ROI by a lesion or to merge or intersect ROIs. Both ROIs must be on the same voxel grid; with sub the order of inputs matters.

| | |
|---|---|
| 📥 **Inputs** | `neuro/rois` ×2 |
| 📤 **Outputs** | `neuro/rois` |
| 🐳 **Container** | `brainlife/fsl:5.0.11` |
| ⚙️ **Resources** | 4 GB memory · 0.25 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.680](https://doi.org/10.25663/brainlife.app.680) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `rois1` | `neuro/rois` | yes | If you want to subtract, the order of inputs matters (first ROI is manipulated). For other functions it does not. |
| `rois2` | `neuro/rois` | yes | ROI directory containing the second ROI (roi_2), e.g. a lesion mask, applied to the first. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `neuro/rois` | ROI directory with copies of both input ROIs and the result <output_roi_name>.nii.gz. |

<details>
<summary><b>⚙️ Parameters</b> (4)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `roi_1` | string |  | File name (without .nii.gz) of the ROI to take from the first ROI input. |
| `function` | enum | `sub` | fslmaths operation applied as roi_1 -<function> roi_2: add, sub (subtract, then clipped to 0-1), mul, div or mas (mask). Options: `add`, `sub`, `mul`, `div`, `mas`. |
| `roi_2` | string |  | File name (without .nii.gz) of the ROI to take from the second ROI input. |
| `output_roi_name` | string |  | File name (without .nii.gz) for the resulting ROI. |

</details>

<!-- brainlife-app:end -->

This app runs fslmaths on two regions of interest (ROI) from another using FSL on the brainlife.io interface. You can set the function to be add, sub, mul, div or mas. One example usage would be to mask an ROI by a lesion using the sub function. 

### Authors
- Hanna Willis (hanna.willis@ndcn.ox.ac.uk)
- Brad Caron 
