# tox24-challenge-project

## Overview

This project was developed for the **Tox24 Challenge**, aimed at predicting the activity of chemical compounds against the transthyretin (TTR) protein using SMILES representations. We employed a hybrid approach that integrates **Graph Convolutional Neural Networks (GCNNs)** to generate electrostatic potential (ESP) surfaces and **3D Convolutional Neural Networks (3D-CNNs)** to predict compound activity from voxelized ESP data.

For detailed explanations on the project methodology, analysis, and results, please refer to the full project report [Predicting_TTR_Activity](Predicting_TTR_Activity.pdf).


## Project Structure

```
tox24-challenge-project/
│
├── data/
│   ├── voxel_data/
│   │   ├── train/                      # Voxelized training data
│   │   └── test/                       # Voxelized test data
│   ├── tox24_challenge_train.csv       # Raw training data
│   └── tox24_challenge_test.csv        # Raw test data
│
├── outputs/
│   ├── checkpoints/
│   │   └── best_model.pth              # Trained model checkpoint
│   ├── intermediate/
│       ├── min_max_scaler.pkl          # Scaler for activity values
│       └── processed_train_dataset.csv
│
├── LICENSE                     
├── Predicting_TTR_Activity.pdf         # Project report
├── project.ipynb                       # Jupyter notebook with code
|── requirements.txt
└── README.md               
```

## Methodology

1. **Data Processing**: SMILES strings are converted to 3D molecular structures using RDKit. The **ESP-DNN** model generates electrostatic potential surfaces, which are voxelized into 3D grids.
2. **Model Architecture**: A 3D Convolutional Neural Network (3D-CNN) is used to predict compound activity based on voxelized ESP data.
3. **Training**: The model is trained on the voxelized data with early stopping and evaluated using Root Mean Squared Error (RMSE). The best model is saved in `outputs/checkpoints/best_model.pth`.

## Results

- **Validation RMSE**: 31.8
- **Baseline RMSE**: 21.8

While our model did not outperform the baseline, it provides a foundation for further exploration and improvements in this domain.

### Installation and Usage

#### Prerequisites

Before starting, ensure that you have the following installed:

- Python 3.6 or higher
- JupyterLab (or Jupyter Notebook)
- Other necessary libraries are listed in `requirements.txt`.


1. **Clone the repository**:

   ```bash
   git clone https://github.com/helenhenryz/tox24-challenge-project.git
   cd tox24-challenge-project
   ```

2. **Create a virtual environment (optional but recommended)**:

   ```bash
   python -m venv env
   source env/bin/activate  # On Windows use `env\Scripts\activate`
   ```

3. **Install required packages**:

   ```bash
   pip install -r requirements.txt
   ```

#### Running the Code

1. **Data Preparation**:

   - Ensure that the data files (`tox24_challenge_train.csv`, `tox24_challenge_test.csv`) are in the `data/` directory.

   - The voxelized data should already be provided in `data/voxel_data/train` and `data/voxel_data/test`.

2. **Run the Jupyter Notebook**:

   - Open `project.ipynb` in Jupyter Notebook or JupyterLab.

   - Run the cells sequentially to execute the data processing, model training, and evaluation steps.

3. **View the Results**:

   - The notebook will display plots and output showing the model's performance.

   - The trained model is saved in `outputs/checkpoints/best_model.pth`.


## Acknowledgements

This project uses the ESP-DNN model to generate electrostatic potential surfaces. The ESP-DNN model is licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), and we acknowledge the work of the authors:

- **Title**: Practical High-Quality Electrostatic Potential Surfaces for Drug Discovery Using a Graph-Convolutional Deep Neural Network
- **Authors**: Prakash Chandra Rathi, R. Frederick Ludlow, Marcel L. Verdonk
- **Journal**: Journal of Medicinal Chemistry
- **Publication Date**: August 27, 2020
- **DOI**: [10.1021/acs.jmedchem.9b01129](https://doi.org/10.1021/acs.jmedchem.9b01129)

We also acknowledge the use of the Tox24 Challenge data provided by [Tetko (2024)](https://doi.org/10.1021/acs.chemrestox.4c00192).

I am beyond grateful to my brother, **Kevin Henry**, whose constant support and technical expertise were the backbone of this project. His patience, thoughtful guidance, and willingness to dive into every challenge with me made this a true brother-sister collaboration. From coding hurdles to late-night problem-solving, he was always there, making this journey both rewarding and memorable. I couldn’t have done it without him!

Additionally, I would like to extend my sincere thanks to **Chris Lumen Ben** for generously providing access to his GPU, which was essential for conducting the computational experiments necessary for this study.


## License

This project is licensed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for more details.


## Contact

For any questions or issues, please contact Helen Henry at helenhenry2025@gmail.com.













