# TranscRater: Transcription Rating Toolkit
An open-source tool for  automatic speech recognition (ASR) quality estimation (QE)

### Description
The tool, allows performing ASR evaluation bypassing the need of reference transcripts and confidence information, which is common to current assessment protocols.
TranscRater consists of two main modules: feature extraction and QE machine learning. 

### Requirements
The requirments:
- "Python" > v2.7
- "json"
- "yaml"
- "SciPy" 
- "sklearn" python library (http://scikit-learn.org/stable/install.html)
- "java v1.8" (http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- "RankLib" v2.6 (https://sourceforge.net/projects/lemur/files/lemur/RankLib-2.6/RankLib-2.6.jar/download)

- "python\_speech\_features" for signal processing toolkit (https://github.com/jameslyons/python_speech_features)
- "RNNLM" recurrent neural network language model toolkit (http://www.fit.vutbr.cz/~imikolov/rnnlm/rnnlm-0.3e.tgz)
- "SRILM" n-gram language model toolkit (http://www.speech.sri.com/projects/srilm/download.html)
- "TreeTagger" part-of-speech tagging toolkit (http://www.cis.uni-muenchen.de/~schmid/tools/TreeTagger/data/tree-tagger-linux-3.2.tar.gz)

### Installation:
The toolkit by itself does not need any installation nor compile. The user needs to download and compile the aforementioned requirments and modify the following environment variables in the configuration file ("config.json"):

- RNNLMDIR= the directory of RNNLM
- SRILMDIR= the directory of SRILM
- TREETAGDIR= the directory of TreeTagger
- RANKLIBDIR= the directory of RankLib

### Usage:
To see the first output of the system with regression models, in the root directory of the package:
```
1. set the config.json
2. ~/TranscRater> python fast_run_RR.py
```

This script will:
```
1. use the data "./data/features/train_*" to train a regression (RR) model,
2. save it into "./RR_Models/"
3. show mean absolute error (MAE) and normalized discounted cumulative gain (NDCG) on the training data
4. use the trained model to predict the WER of the "./data/test_*"
5. save the predicted WER on "./results/test.pwer" and the predicted ranks on "results/test.prank"
6. show MAE and NDCG on the test data
```

To see the first output of the system with machine-learned ranking (MLR) models:
```
1. download RankLib-2.6.jar and set its path in config.json
2. ~/TranscRater> python fast_run_MLR.py
```

This script will:
```
1. use the data "./data/features/train_*" to train a ranking model,
2. save it into "./MLR_Models/"
3. show NDCG on the training data
4. use the trained model to predict the ranks on "./data/features/test_*"
5. save the predicted ranks on "results/test.prank"
6. show NDCG on the test data
```
For a complete process on a real data set, starting from transcripts and feature extraction please go to "./egs/CHiME3/" directory where we use the data of the 3rd CHiME challenge train and test the ASR QE models. 

### Contacts
[Shahab Jalalvand](https://hlt-mt.fbk.eu/people/profile/jalalvand), Fondazione Bruno Kessler, Italy (shahabjld2@gmail.com)


