# ECG-Signal-Processing
## Introduction:

Electrocardiography (ECG) is a fundamental diagnostic tool used to record the electrical activity of the heart. It plays a crucial role in detecting and monitoring various cardiac conditions, including arrhythmias, coronary artery disease, and heart attacks. This underscores the importance of reliable ECG analysis for early detection and treatment of heart conditions.
ECG signals are typically very weak, with amplitudes in the range of 5 mV or lower. Due to this low signal strength, amplification is necessary to make the signal interpretable. However, ECG recordings are also highly susceptible to noise from various sources, such as power line interference, baseline wander, and muscle artifacts. Effective signal processing is required to filter out these disturbances and extract meaningful information from the ECG waveform.

## Objective:
The objective of this project is to design and simulate an ECG signal processing system capable of generating a realistic amplified ECG waveform and effectively filtering out noise. Firstly a  ECG signal prototype is created to represent the PQRST components with proper amplitude and timing characteristics. To simulate real-world conditions, noise sources such as power line interference (50/60 Hz) and baseline wander are introduced . After this an analog signal processing circuit is designed using LTSpice, incorporating amplification, high-pass filtering to remove baseline drift, low-pass filtering to eliminate high-frequency noise, and a notch filter to specifically target power line interference. This model ensures that real ECG signals can be processed efficiently, allowing for precise measurement of key intervals such as the PR interval, QRS duration, and QT interval, which are crucial for diagnosing heart conditions.

<p align="center">
  <img src="https://github.com/user-attachments/assets/87b50219-4149-498c-a139-54f061fd0945" 
       alt="Screenshot 2025-06-28 154723" 
       width="300"/>  
  
### Standard values :  
PR interval < 0.2 sec  <br>
QRS interval < 0.14 sec  <br>
QT interval < 0.45 sec  <br>
For our simulation RR = 0.826 sec  <br>
Hence, heart beat rate (bpm) = 72, which is normal heart rate.

## 1.Signal Generation 
In this task, a synthetic ECG signal was generated along with various noise components to closely mimic real-world conditions. The ECG waveform consists of characteristic features such as the P wave, QRS complex, and T wave. To replicate realistic scenarios, different types of noise were introduced into the signal as given below.The ECG signal was generated using Python in Google Colab for efficient computation and visualization. The complete code for this simulation has been attached in the next file for reference.

