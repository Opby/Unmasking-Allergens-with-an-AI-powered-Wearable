# Introduction
* Develop an AI-powered wearable device to detect human’s allergic reactions by recording and analyzing cough and sneeze types and patterns. A pre-trained AI model is used to identify unique characteristics of cough and sneeze associated with allergies. By correlating this data with location-based allergen information, the project aims to provide a novel and accessible way for everyone to detect their allergens without having to visit medical clinics.
<img width="447" alt="Screen Shot 2025-04-07 at 5 26 17 PM" src="https://github.com/user-attachments/assets/b33b5ce2-3548-4f02-b4f5-18b4783f4aec" />

# Hardware Platform and AI training Platform
* We used Seeed Wio terminal as the hardware platform and Edge Impulse as the model training platform

# Methods - Cough and sneeze recognition with Mel-Spectrogram and Convolutional Neural Network
* Mel-Spectrogram can effectively extract hidden features of sound and visualize as an
image
All audio signals are pre-processed to 1 s long
16kHz sampling is used for sampling to ensure key features are kept
Short-time Fourier transform (STFT) is used to convert time series into frequency domain
and then converted from the linear frequency scale to the logarithmic Mel-scale
Mel-Filter bank is used to get the eigenvector as the distribution of signal energy on the
Mel-scale frequency
The recognition loss function of the model is used to determine optimal settings for
minimal loss:
Lrec=−1nΣ[ylnˆy+(1−y)ln(1−ˆy)]
* Convolutional Neural Network (CNN) Model can effectively extract features from images
and complete recognition
The convolutional layer is the key of a CNN model to reduce the parameters of the
model while keeping the accuracy. This is especially important as our model will be
deployed to a small wearble devices
The formula for the convolutional layer is:
<img width="277" alt="Screen Shot 2025-04-07 at 5 34 24 PM" src="https://github.com/user-attachments/assets/b24a8d80-f5f7-45b2-9d99-fbe98acbaa5f" />

After each convolutional layer, we conduct batch normalization to make the outputs of
the convolutional layer stay identically distributed, which can improve the performance
of the model
<img width="1133" alt="Screen Shot 2025-04-07 at 5 34 35 PM" src="https://github.com/user-attachments/assets/853b1e43-5532-4844-9d37-36df8961d35d" />


# AI model training and deployment
* We used a mix of public dataset and recorded data from human volunteers
Three types of audio data: background, coughing and sneezing
 ~30 samples for each type are from human volunteers
~150 samples for each type are from public dataset
<img width="468" alt="Screen Shot 2025-04-07 at 5 32 11 PM" src="https://github.com/user-attachments/assets/f5a2fe1c-6489-4c99-93b3-c58ae798da23" />

# AI model accuracy
* Model accuracy:
Background ~91%
Coughing ~80%
Sneezing ~97%
<img width="683" alt="Screen Shot 2025-04-07 at 5 36 37 PM" src="https://github.com/user-attachments/assets/379ebf1a-3f90-4486-8195-34affd988324" />
