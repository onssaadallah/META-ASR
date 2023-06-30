# META-ASR
## Automatic speech recognition (ASR) is a revolutionary technology that allows computers to transcribe spoken language into written text without any human intervention.
However, to implement ASR effectively, it is crucial to select a suitable system that can
handle diverse types of spoken data.
Currently, there are several pretrained ASR models available, but no single model can
effectively handle all types of spoken data. In this thesis, we propose a novel approach:
the development of a meta-ASR system capable of analyzing audio features and selecting
the most appropriate pretrained ASR model from two state-of-the-art models, QuartzNet
15x5 and Wave2Vec 2.0.
This project was undertaken at AMZI Smart Solutions with the hypothesis that our
Meta-ASR system would outperform using each individual model in isolation.
To evaluate the effectiveness of these approaches, we employed the word error rate
(WER) metric, which measures the accuracy of the transcriptions, on several open-source
audio datasets.
The results of our evaluation demonstrated that the meta-ASR approach performed
significantly better. This success can be attributed to its flexibility in adapting to different
audio characteristics and its ability to process diverse audio types in a customized manner,
rather than using a one-size-fits-all approach.
Keywords: Automatic speech recognition, meta-ASR, audio features, QuartzNet
15x5, Wave2Vec 2.0, word error rate.
