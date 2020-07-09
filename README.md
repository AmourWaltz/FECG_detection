# FECG_detection

The fetal ECG signal is pre-processed with ICA to obtain a signal source with less interference from maternal ECG. The fetal heartbeat segments as positive samples and the background segments as negative samples are intercepted to make a training set and train the model with CNN-LSTM.

It’s the first attempt to detect the fetal ECG heartbeat using CNN-LSTM and active learning to implement an inter-patient model, while traditional methods could only complete in intra-patient method.

It has reached an accuracy of 92% (compared with state-of-the-art traditional method Wavelet Analysis which has reached 89% on the same database from PhysioNet Computing in Cardiology Challenge 2013).

