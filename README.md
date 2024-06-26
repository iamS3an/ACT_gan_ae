# ACT_gan_ae

This repository contains code for generating and analyzing adversarial datasets for intrusion detection, specifically focusing on the UNSW-NB15 dataset.

## Dataset Description
### Download Link: [Here](https://drive.google.com/file/d/1hwFgA6_NKJksASGJVySBCFl1fOy_0PkK/view?usp=drive_link)
- **Training Set:** UNSW_NB15_training-set.csv
- **Testing Set:** UNSW_NB15_testing-set.csv

Both datasets should be placed in the `data/0_ori/` directory.

## Code Modules

### Data Preprocessing
- `preprocess.py`: Generates preprocessed data and stores it in `data/1_preprocess/`.

### Conditional Generative Adversarial Network (CGAN)
- `gan.py`: Generates CGAN adversarial data and stores it in `data/2_cgan`.

### Autoencoder
- `autoencoder.py`: Generates autoencoder adversarial data and stores it in `data/3_autoencoder/`.

### Deep Neural Network (DNN) Classifier (Keras)
- `dnn_keras.py`: Provides classification results for original data and adversarial data generated by CGAN and autoencoder.

### Adversarial Data Detection
- `adv_det.py`: Removes original benign/malicious labels, assigns new labels (0 for original, 1 for adversarial), and performs adversarial data detection.
- `preCT_adv_det.py`: Merges autoencoder's adversarial data with original data, reassigns labels, and outputs to `data/4_preCT/`.
- `adv_det_CT.py`: Detects adversarial data after calculating p-values using the algorithm from [ct-value](https://github.com/nervouswizard/ct-value).

## Experiment Results
- **P-value Calculation:** The `ct-value` repository is used to calculate p-values for data in `data/4_preCT/`. The results are stored in `ct-value/data/3_DataWithPvalue/p-value/train.csv` and `ct-value/data/6_mapped_test/pvalue_test.csv`, which are then placed back in `data/5_CTed/`.

- **Adversarial Data Detection Experiments:**
  - Results for original and CT (p-value calculated) versions of adversarial data detection experiments are stored in `adv_det.txt` and `adv_det_CT.txt`, respectively.
  - These files contain experimental data for different epochs (1, 3, 5, 10, 20) of training.

For any inquiries or issues, please contact the repository owner.

