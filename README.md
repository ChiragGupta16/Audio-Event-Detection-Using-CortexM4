# Audio-Event-Detection-Using-CortexM4


### Overview

Board Used - STM32F407-DISC1 <br>
Processor - ARM Cortex M4 <br>

 Audio Event Detection (AED): 
It focuses on the automatic identification and classification
of sounds occurring within continuous audio streams.
Features such as Mel-Frequency Cepstral Coefficients (MFCC)
are extracted from the audio stream and passed to ML models
for detection. This method uses Support Vector Machines (SVM)
to detect alarm bell sound, which acts as a trigger. The model
was trained on MFCC features extracted with the help of CMSIS-DSP. Alarm Bell was chosen because it is readily
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
of the PD12 pin. If the desired Alarm bell sound is detected, it
is set to high, else low.

### Procedure for Custom AED
1. Download and install softwares such as Tera Term. <br>
2. In the src file. comment out the inference and un-comment the sendMFCC function. <br>
3. Use a Micro-USB cable to send data to PC and save it using TeraTerm. <br>
4. Use scikit-learn to train SVM and print the parameters. <br>
5. Copy and replace the paramters in the main.c file. <br>
6. Again comment out the sendMFCC function and un-comment the inference part. <br>

### If you find this project helpful, please consider giving it a ⭐! <br>
### In case of any queries, please feel free to drop a mail at chiragguptactc@gmail.com <br>
### Thanks for going through this project. Happy coding :)

