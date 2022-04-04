# Unified Implicit Neural Stylization
Implementation of "Unified Implicit Neural Stylization".

## Installation

We recommend users to use `conda` to install the running environment. The following dependencies are required:
```
pytorch=1.7.0
torchvision=0.8.0
cudatoolkit=11.0
tensorboard=2.7.0
opencv
imageio
imageio-ffmpeg
configargparse
scipy
matplotlib
tqdm
mrc
lpips
```

## Data Preparation

To run our code on NeRF dataset, users need first download data from official [cloud drive](https://drive.google.com/drive/folders/128yBriW1IG_3NJ5Rp7APSTZsJqdJdfc1). Then extract package files according to the following directory structure:

```
├── configs
│   ├── ...
│
├── datasets
│   ├── nerf_llff_data
│   │   └── room
│   │   └── horns   # downloaded llff dataset
|   |   └── ...
|   ├── nerf_synthetic
|   |   └── lego
|   |   └── chair    # downloaded synthetic dataset
|   |   └── ...
```
The last step is to generate and process data via our provided script:
```
python gen_dataset.py --config <config_file>
```
where `<config_file>` is the path to the configuration file of your experiment instance. Examples and pre-defined configuration files are provided in `configs` folder.

## Testing

After generating datasets, users can test the conditional style interpolation of INS+NeRF by the following command:
```
bash scripts/linear_eval.sh
```

Users can also generate new views using given camera coordinates:
```
bash scripts/infer_horns.sh
```