# VOC-EnthVapML

<img width="759" alt="Screenshot 2025-04-11 at 14 37 23" src="https://github.com/user-attachments/assets/f16d78a5-f224-4741-b102-5047d595d239" />

This is the repository for the research project: "Data-Driven, Explainable Machine Learning Model for Predicting Volatile Organic Compounds’ Standard Vaporization Enthalpy" DOI: https://doi.org/10.1016/j.chemosphere.2024.142257

The complete dataset is doposited in Zenodo: https://zenodo.org/doi/10.5281/zenodo.11127879

## File Overview

Database

- `VOC-Database.csv`: Complete dataset with descriptor calculations to run the model

- `Database-Global.xlsx`: Raw complete dataset with internal and external sources

- `desc_VOC-RF.csv`: Descriptor group categorisation

Scripts

- `rdkit_conversion_vap.py`: Calculation of desired RDKit descriptors using the raw database

- `dVap-Model-Testing.py`: Model calculations using desired algorithms with all calculated descriptors

- `VOC-Model-Testing.py`: Model calculations for VOC with all calculated descriptors and hyperparameter optimization

- `dVap-Family-Group-Testing.py`: Model calculations for VOC descriptor groups and chemical family testing

Results

- `VOC-ML-Full-Results.xlsx`: File including all model results presented in the paper (including permutation importance, model statistical performance and descriptors group performance determinations)

- `dVap-ML-Dev-Results.xlsx`: File including model results for preiction optimization of the standard enthalpy of vaporization (including permutation importance, model statistical performance and descriptors group performance determinations).

## Reusing this code

Tested on Linux Debian 12 (Bookworm).

Prerequisites: `git` and a Python 3.11 or later interpreter (numpy 2.3 requires Python 3.11). You can get those using Docker with: `docker run --rm -it -v $PWD:/app -w /app python:3.11-bookworm bash`.

Set up your virtual enviroment with:

```sh
python3 -m venv venv
source ./venv/bin/activate
pip install -U -r requirements.txt
```

To validate that your environment reliably reproduces the results of the authors, execute the test script:

```
python ./Scripts/VOC-Model-Testing.py
```

this will generate a `Results/VOC-results.csv` with should match (with a certain TBD floating point tolerance) the file `Results/VOC-results.csv` in the repo; verify the differences with:

```
git diff Results/VOC-results.csv
```
