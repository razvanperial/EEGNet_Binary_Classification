# Using EEGNet architecture in binary classification

This repository contains the code necesarry for running the EEGNet Deep Learning architecture model on a dataset composed of EEG signals, with the purpose of performing a binary classification.

For the installation of EEGNet, follow this repository [link](https://github.com/vlawhern/arl-eegmodels) .

## Requirements

- Python 3.7 or newer
- Tensorflow 2.0 or newer
- Numpy
- Matplotlib
- Scikit-learn
- Scipy

## Dataset

The data is composed into 8 main datasets, with suggestive names. The classification was then made between the `P` (clinical subjects) and `S` (control sibjects) data, basedon the EEG signals. For privacy reasons, the data is not available in this repository, but with small modifications to the code, you can use your own data.

## Code

This code is the accumulation of applying numerous different filters and changes to the original dataset, in order to find the best possible results. The code is divided into the following directories, each containing a different approach to the problem.

Also note thatt for each directory which contains models that are trained, the general structure is to have a `scripts` directory with a `z_run_all.ipynb` file, which is the main file that should be run if you want to run all the scripts available in that directory. Of course, you can also run all the scripts individually. Each script will create a `.txt` file which contains the results of the model. Most of the result files still have the original results from the first time the model was run, so if you want to run everything again consider emptying the result files first.

Directories:

- `naive_classification` - Contains the code for the basic binary classification on the data set, without any changes to the data.
- `capped_data` - Here, there exists two approaches:
    - `first_500_samples` - The model was only trained on the first 500 samples of each EEG signal.
    - `first_500_no_disc` - The same approach as above, but this time discontinuities in the EEG signals were removed from the data.
- `first_5_subjects` - The model was trained using only the first 5 subjects from each group (P and S). Only the first 500 samples of each EEG signal were used, and the discontinuities were removed.
- `fewer_channels` - The model was trained using only 4 out of 14 channels. Same as above, only the first 500 samples of each EEG signal were used, and the discontinuities were removed.
- `bandpass` - The model was traiend using a bandpass filter on the data, with different frequency ranges being used. Same as above, only the first 500 samples of each EEG signal were used, and the discontinuities were removed.
- `conditions` - Using an extra dataset, the classification problem became more complex, having to now classify between 6 different classes, since each previous class now had 3 different subclasses (conditions).
- `visualisation` - In this folder, there exist different approaches to visualise certain aspects of the data:
    - `feature_extraction` - Here, the model was trained, and then for a random EEG signal that would run through the CNN, the output of each layer was saved and plotted, for better visualisation of what the model is doing.
    - `visualise_raw_clean`- 2 files being used for comparison in the data set between the "raw" data and the "clean" data, after some other filters were applied to it.
    - `visualise_S_P` - 2 files being used for visualisation of the 2 kinds of subjects in the data set, the `P` and the `S` subjects.
- `functions` - This folder contains the functions that were used in the other scripts, for better organisation of the code.
