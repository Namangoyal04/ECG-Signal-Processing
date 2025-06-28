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
In this task, a synthetic ECG signal was generated along with various noise components to closely mimic real-world conditions. The ECG waveform consists of characteristic features such as the P wave, QRS complex, and T wave. To replicate realistic scenarios, different types of noise were introduced into the signal as given below.The ECG signal was generated using Python in Google Colab for efficient computation and visualization. The complete code for this simulation has been attached in the file for reference.

![Screenshot 2025-06-28 222218](https://github.com/user-attachments/assets/19bf6141-0097-4378-b211-baba03fdb960)

## 2.Noise Addition to ECG Signal 
* **Power Line Interference (50/60 Hz,0.5mV)**: This noise, primarily caused by electromagnetic interference from electrical devices, generally falls within the range of 50 Hz (Europe, Asia) or 60 Hz (North America),with amplitude less than 1mv. A Notch Filter was later used to remove this interference.
* **Baseline Wander (0.1–0.5 Hz,0.2mV)**: Low-frequency drift resulting from respiration and patient movement. In our case, we subjected these noises to ECG wave to meet real word conditions using sin wave sources with frequency and amplitude matching with the frequencies of noises mentioned . A Third-Order High-Pass Filter was implemented to eliminate this effect.
<p align="center">
  <img src="https://github.com/user-attachments/assets/8b9e381b-2820-4530-88f0-d7cbae6c4688" 
       alt="Screenshot 2025-06-28 154723" 
       width="300"/>  
  
 ## 3.Amplification of input signal & Filtering out the noise 
 ###   A.Instrumental amplifier (Gain=1000)
 An Instrumentation Amplifier (IA) is used in ECG signal processing because:
* It provides high gain and high common-mode rejection ratio (CMRR).
* It amplifies small differential signals (e.g., ECG signals from the body).
* An inverting op-amp of unity gain is also cascaded to invert the output.
* Gain= (1+ 2R2/R1)*(R4/R3), here gain =1000, input in range of mV

### B. Notch Filter (50/60 Hz)
* Purpose: Removes power line interference caused by electrical sources 
* Why It’s Used: Power line noise is a common and strong interference in ECG recordings due to improper grounding or nearby electrical devices. A notch filter specifically    targets this frequency, significantly reducing its impact without affecting other components of the signal

### C. LowPass Filter (Cutoff ~ 150 Hz)
* Purpose: Retains the essential ECG frequency range while removing unnecessary high-frequency components.
* Why It’s Used: The upper cutoff (150 Hz) eliminates muscle artifacts and high-frequency disturbances beyond the ECG signal’s required range.

### D. Third-Order High-Pass Filter (Cutoff ~0.5 Hz)
* Purpose: Eliminates baseline drift and very low-frequency noise while preserving the PQRST components.
* Why a Third-Order Filter?
* Higher-order filters provide a sharper roll-off, meaning they more effectively remove unwanted frequencies without distorting important signal components.
* A third-order high-pass filter offers a better transition band compared to a first- or second-order filter, ensuring minimal distortion in the ECG waveform.
* Effect: Removes slow-varying baseline fluctuations, making the ECG signal clearer and more analyzable.
* Also the gain of 2 is provided because of  attenuation in gains while passing from previous filters 

#### By combining these filters, we achieve a clean ECG signal that retains the necessary features for medical analysis while eliminating common noise sources.

## Final Cascaded Circuit 
![Screenshot 2025-06-28 223353](https://github.com/user-attachments/assets/9bf3b7b4-d8df-45c9-a03c-99dd4c3e3f8d)

## Waveforms
### INPUT SIGNAL (in mV):
![Screenshot 2025-06-28 223628](https://github.com/user-attachments/assets/22f32034-5d1a-487d-b5a3-0ca792af5487)

### SIGNAL WITH NOISE:
![Screenshot 2025-06-28 223639](https://github.com/user-attachments/assets/a935121e-bf6f-4357-8b1d-0c1f042c401a)

### AMPLIFICATION & NOTCH FILTER:
![Screenshot 2025-06-28 223649](https://github.com/user-attachments/assets/14db6b52-2ad6-4daf-a193-23c92342e9c2)


### OUTPUT WAVEFORMS
![Screenshot 2025-06-28 223701](https://github.com/user-attachments/assets/9531acd3-3499-435b-99b6-ba2fb7ed96d1)

### CALCULATED VALUES OF INTERVALS :
* PR interval = 0.163 sec
* QRS interval =0.137 sec
* QT interval =0.44 sec
* For our simulation RR = 0.825 sec
* Therefore , heart beat rate (bpm) =60/0.825= 72 


