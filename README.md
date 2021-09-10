# Respiratory Disease Detection
![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)

Respiratory sounds are important indicators of respiratory health and respiratory disorders. The sound emitted when a person breathes is directly related to air movement, changes within lung tissue and the position of secretions within the lung.

This digital data opens up the possibility of using machine learning to automatically diagnose respiratory disorders like asthma, pneumonia and bronchiolitis, to name a few.

## Dataset
The Respiratory Sound Database was created by two research teams in Portugal and Greece. It includes 920 annotated recordings of varying length - 10s to 90s. These recordings were taken from 126 patients. There are a total of 5.5 hours of recordings containing 6898 respiratory cycles - 1864 contain crackles, 886 contain wheezes and 506 contain both crackles and wheezes. The data includes both clean respiratory sounds as well as noisy recordings that simulate real life conditions. The patients span all age groups - children, adults and the elderly.

This Kaggle dataset includes:

- 920 .wav sound files
- 920 annotation .txt files
- A text file listing the diagnosis for each patient
- A text file explaining the file naming format
- A text file listing 91 names (filename_differences.txt )
- A text file containing demographic information for each patient

**The Dataset can be found on Kaggle [here](https://www.kaggle.com/vbookshelf/respiratory-sound-database "here").**

## Notebooks
#### Preprocessing
As mentioned the respiratory cycle timings are mentioned in annotated files, so we **extract parts** of audio files which consist of respiratory cycles of a patient. Also, each respiratory cycle is not so same length, they **vary from 10s to 90s**, some of which are outliers as well, so we find mean length and trim all cycles to this mean length using  **Librosa** module for loading audio files and **Soundfile** module for writing to output path of new audio files created.

#### Balancing
After preprocessing the dataset will be imbalanced towards one or more classes this inbalance must be dealt with using different techniques, this notebook uses **stratify** parameter of sklearn **train_test_split** to balance both test and train datasets on equal fraction of classes.

#### Feature Extraction
Extracting features from audio sample is a task of its on, so using 3rd parties libraries help out a lot, here [Librosa](https://librosa.org/doc/latest/index.html "Librosa") is used to extract three most important features namely [MFCC](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum "MFCC"), [CHROMA STFT](https://en.wikipedia.org/wiki/Chroma_feature) and [MEL SPECTROGRAM](https://en.wikipedia.org/wiki/Mel_scale "MEL SPECTROGRAM")

#### Modeling
Each feature is an **matrix of frequencies** which is treated as an heatmap of frequencies and passed through different model paths for **specific training** and then concatenated for **general optimisation** and classification. The model is Keras **Function API Convotional Model** with BatchNormalization and ReLU activation.

#### Results
![img](https://imgpile.com/images/NSBp7W.png)
<br>
<br>
![img](https://imgpile.com/images/NSBSPP.png)
<br>
<br>
![img](https://imgpile.com/images/NSBZO1.png)
