# Audio-Event-Detection-Using-STM32

 Audio Event Detection (AED): 
It focuses on the automatic identification and classification
of sounds occurring within continuous audio streams.
Features such as Mel-Frequency Cepstral Coefficients (MFCC)
are extracted from the audio stream and passed to ML models
for detection. This method uses Support Vector Machines (SVM)
to detect desk bell sound, which acts as a trigger. The model
was trained on MFCC features extracted with the help of CMSIS-DSP. Desk Bell was chosen because it is readily
available, and its consistent tone lets us lower the sampling
rate and reduce frame overlapping, saving both RAM and
computational time. Furthermore, it also avoids the challenges
such as phoneme distortion and prosody which comes with
human speech classification. A PDM microphone has been
utilised to sample the audio. It was configured using I2S in
Master receive mode to operate at 8Khz. A circular DMA
was configured for continuous PDM data transfer from the
peripheral to the memory buffer. A total of 2048 PCM samples
are collected using the PDM2PCM library and are divided
into five overlapping frames of 512 samples. MFCCs are
extracted using 20 Mel filter banks and a Hamming window,
producing 13 coefficients per frame. The resulting 65 features
are classified using an SVM, whose output controls the state
of the PD12 pin. If the desired desk bell sound is detected, it
is set to high, else low.
