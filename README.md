# Petrographic Thin-Section Analysis with SAM2

A Python workflow for pore detection, grain segmentation, and quantitative analysis of petrographic thin-section images using **SAM2** and classical image-processing methods.

The pipeline was developed for resin-impregnated thin sections in which pore space is highlighted with blue or teal epoxy.

## Features

* Blue/teal epoxy pore detection
* Optional rock/background masking
* CLAHE contrast enhancement
* Tiled SAM2 grain segmentation
* Filtering of invalid and duplicate masks
* Recovery of missed grains using point prompts
* Splitting of merged grains
* Fine-grain recovery
* Grain morphology measurements
* Porosity and local porosity analysis
* Grain-size and roundness heatmaps
* CSV, Excel, NumPy, and image export

## Workflow

```text
Thin-section image
        ↓
Pore and rock masking
        ↓
SAM2 grain segmentation
        ↓
Mask filtering and recovery
        ↓
Merged-grain splitting
        ↓
Final grain instances
        ↓
Morphometric analysis
```

## Measurements

The workflow calculates properties such as:

* Area
* Equivalent diameter
* Perimeter
* Major and minor axis length
* Circularity
* Aspect ratio
* Elongation
* Solidity
* Orientation
* Porosity
* Grain-size distribution

## Usage

Select the sample in the configuration section:

```python
SAMPLE = "G50"
```

Set the directory containing the input images:

```python
DATA_DIR = "/path/to/data"
```

Then run the notebook cells in order.

A CUDA-capable GPU is recommended for SAM2 inference.

## Installation

```bash
pip install -r requirements.txt
```

SAM2 can also be installed directly from its official repository:

```bash
pip install git+https://github.com/facebookresearch/sam2.git
```

## Data

Raw petrographic images and research annotations are not included in this repository.

The pipeline currently contains configurations for:

* G50
* G-57
* N75-1
* N302
* N304
* T-51
* T-51_2

Additional samples can be added through the configuration dictionary.

## Outputs

The workflow can generate:

* grain segmentation images
* labeled grain masks
* grain polygons
* grain measurement tables
* porosity maps
* grain-size distributions
* grain-size heatmaps
* roundness heatmaps

## Future Work

Future development will focus on reducing sample-specific rules and improving generalization to previously unseen petrographic images.

Possible directions include:

* expanding the dataset with additional thin-section samples
* manually validating and correcting generated grain and pore masks
* using verified masks as training labels
* fine-tuning SAM2 or training a petrography-specific segmentation model
* semantic segmentation of pore space
* instance segmentation of individual grains
* evaluation on completely unseen thin-section samples
* automated quality control for segmentation results

The long-term goal is to move toward a workflow in which a trained model can directly generate reliable grain and pore segmentations, followed by conventional quantitative morphometric analysis.

## Acknowledgements

This project uses **Segment Anything Model 2 (SAM2)** developed by Meta AI, together with open-source scientific Python libraries including OpenCV, NumPy, pandas, SciPy, scikit-image, Shapely, Matplotlib, PyTorch, and `segmenteverygrain`.

Please refer to the original projects for license and citation information.
