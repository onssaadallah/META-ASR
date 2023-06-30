# Automated Speech Recognition Using Meta-Learning (META-ASR)
Automatic speech recognition (ASR) is a revolutionary technology that allows computers to transcribe spoken language into written text without human intervention.
However, to implement ASR effectively, it is crucial to select a suitable system that can
handle diverse types of spoken data.
Currently, there are several pre-trained ASR models available, but no single model can
effectively handle all types of spoken data. In this thesis, we propose a novel approach:
the development of a meta-ASR system capable of analyzing audio features and selecting
the most appropriate pre-trained ASR model from two state-of-the-art models, QuartzNet
15x5 and Wave2Vec 2.0.
This project was undertaken at AMZI Smart Solutions with the hypothesis that our
Meta-ASR system would outperform using each model in isolation.
To evaluate the effectiveness of these approaches, we employed the word error rate
(WER) metric, which measures the accuracy of the transcriptions, on several open-source
audio datasets.
The results of our evaluation demonstrated that the meta-ASR approach performed
significantly better. This success can be attributed to its flexibility in adapting to different
audio characteristics and its ability to process diverse audio types in a customized manner,
rather than using a one-size-fits-all approach.
Keywords: Automatic speech recognition, meta-ASR, audio features, QuartzNet
15x5, Wave2Vec 2.0, word error rate.
## Meta ASR Pipeline
![-](https://github.com/onssaadallah/META-ASR/assets/44116045/2014ad88-fc15-4dd2-a96d-c8f7e340088a)

## Repository files
The project is divided into three main directories:
The data Annotation directory presents the metadata creation steps:
   1- Audio Collection.ipynb: Collect the audio data from YouTub by converting each video into audio and splitting each audion into sequences of chunks. we save the audio data in the folder called "Audio_Data".
   Audio_Data Directory Structure
   The "Audio_Data" directory is organized into multiple folders. Each folder represents a specific video and contains sequences of audio chunks derived from that video.

   2-FeatureExtraction.ipynb: Extract the distribution satistical (min, max, mean, median, Q1, Q3)features from the most commonly used signal audio features:
             META_FEATURES={
                0:'MFCC',
                1:'spectral_centroid',
                2:'spectral_bandwidth',
                3: 'zero croinssing rate',
                4:'Length',
                5:'Duration',
                6:'Sample_Rate'}
                

    This notebook generates two types of data :

        --> Raw Metadata: This metadata presents the meta-feature extraction from the raw signal audios without employing the signal audio pre-processing techniques.

        -->  Preprocessed Metadata: This metadata presents- the meta-feature extraction from the pre-processed signal audios  (reduce noise and normalize).

    3-AudioDataClustering.ipynb: 
      This notebook presents the clustering process. So we cluster audios based on their meta-features.
      The purpose of applying clustering is to reduce the annotation cost. We apply the clustering process on the two types of metadata (Raw Metadata, Preprocessed Metadata)

    4- ManualAnnotaion.ipynb:
       The manual annotation which involves extracting reference audio from each cluster and manually transcribing these audio samples. This step enables us to create a ground truth dataset. W3e transcript these reference audios by the selected candidate pre-trained ASR models such as QuartzNet15x5BaseEn’, ’wav2vec2-large-960h-lv60-self’,wav2vec2-large-50-self, and the Speech Recognition of the Google engine. We compare the transcriptions generated by these ASR models and select the one with the lowest word error rate (WER) as the best pre-trained model for each audio sample.

    5-Labling_Data.ipynb: Labeled the two metadata with a pre-trained ASR model. The candidate ASR pre-trained models are:
      #define the candidate pre_trained models
      CANDIDATE_PRE_TRAINED_MODELS={
        0:"QuartZnet_Model",-
        1: "Wav2Vec50_Model",
        2:"Wav2Vec960_Model",
        3: "speech2Text_Model"}
    

       => We save the main metadata which presents the final version of the Metadata in the Main_Dataset directory :
          - Main_PreProcessedMetaData.csv
          - Main_RawMetaData.csv


* Meta_Modeling directory presents the meta Model creation steps:
   1-DataExploring.ipynb: Analyzing and exploring the two main metadata (Main_PreProcessedMetaData.csv, Main_RawMetaData.csv)
   The objective here is to define the classification task for each metadata

   2-Meta_Model.ipynb: Employing the classification statistical machine learning models such as    'DecisionTree','RandomForest', and 'Knn'. select the best classification statistical model based on the evaluation metric F1-SCORE.

* Meta_Model_Evaluation directory presents the evaluation process of the Meta_ASR:
   TestModel.ipynb: The evaluation process of the meta-model involves testing its performance on the ground truth data by transcribing the text from each input audio and computing the Word Error Rate (WER).

## Tools and Frameworks Used    

- Pandas
- Youtub-dl
- pydub
- librosa
- Nemo
- Scikit-learn
- jiwer
- transformers
- Torch
- pickle
- wavio
- plotly



   







          



