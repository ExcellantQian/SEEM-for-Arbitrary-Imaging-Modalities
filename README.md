<div align="center"> 

## AIM-SEEM: Adapting SEEM for Open-Vocabulary Terrain Segmentation Across Arbitrary Imaging Modalities

</div>

## Introduction

The advancement of terrain segmentation technology critically determines the performance of environmental perception. However, due to the diversity of real-world scenarios, conventional segmentation methods struggle to handle arbitrary imaging modalities and meet the dynamic requirements of open-vocabulary learning. To address these challenges, this paper proposes AIM-SEEM, an open-vocabulary terrain segmentation framework capable of processing arbitrary imaging modalities and their combinations. First, we integrate an RGB-Oriented Aligner (ROA) with a Cross-Modal Blending Adapter (CMBA) to achieve alignment across arbitrary modal dimensions and input counts. Nevertheless, the introduction of arbitrary imaging modalities disrupts the original open-vocabulary capability of SEEM. To mitigate this, we introduce a Visual-Guided Text Tuner (VGTT), which realigns visual features and textual embeddings within SEEM to adapt to diverse modal inputs. Experimental results demonstrate that AIM-SEEM consistently outperforms existing semantic segmentation models supporting arbitrary modalities. 

## Updates
- [x] 01/2026: init repository and release the code.

## AIM-SEEM model

<div align="center"> 

![AIM-SEEM](overview.png)

**Figure:** Overall architecture of AIM-SEEM model.

</div>

## Environment

- Install openmpi (required for mpirun):
  ```sh
  sudo apt install libopenmpi-dev
  ```
- Install the requirements:
  ```sh
  pip install -r assets/requirements/requirements.txt
  pip install -r assets/requirements/requirements_custom.txt
  ```

## Data preparation
Download the dataset:
- [MCubeS](https://github.com/kyotovision-public/multimodal-material-segmentation), for multimodal material segmentation with RGB-Aolp-Dolp-Nir modalities.
- [DELIVER](https://github.com/jamycheung/DELIVER), for DELIVER dataset with RGB-Depth-Event-Lidar modalities.

Then, put the dataset under `data` directory as follows:

```
data/
├── MCubeS
│   ├── polL_color
│   ├── polL_aolp_sin
│   ├── polL_aolp_cos
│   ├── polL_dolp
│   ├── NIR_warped
│   ├── NIR_warped_mask
│   ├── GT
│   ├── SSGT4MS
│   ├── list_folder
│   └── SS
├── DELIVER
│   ├── depth
│   │   ├── cloud
│   │   │     ├── test
│   │   │     ├── train
│   │   │     └── val
│   │   ├── fog
│   │   ├── night
│   │   ├── rain
│   │   └── sun
│   │   
│   ├── train
│   ├── event
│   ├── hha
│   ├── img
│   ├── lidar
│   └── semantic

```

## Training

Before training, please download [pre-trained SEEM](https://huggingface.co/xdecoder/SEEM/tree/main), and put it in the correct directory following this structure:

```text
pretrained/
├── seem_focalt_v1.pth
├── seem_focall_v1.pth
└── ...
```

To train AIM-SEEM model, please update the appropriate configuration file in `configs/` with appropriate paths and hyper-parameters. Then run as follows:

```bash
bash train.sh
```

## License

This repository is under the Apache-2.0 license. For commercial use, please contact with the authors.


## 🔈 Acknowledgements
Our codebase is based on the following Github repositories. Thanks to the following public repositories:
- [Segment-Everything-Everywhere-All-At-Once](https://github.com/UX-Decoder/Segment-Everything-Everywhere-All-At-Once)
- [SEEM-Adapter](https://github.com/david-rohrschneider/SEEM-Adapter)

**Note:** This is a research level repository and might contain issues/bugs. Please contact the authors for any query.
