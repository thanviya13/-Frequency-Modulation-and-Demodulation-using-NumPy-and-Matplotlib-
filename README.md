<img width="892" height="1032" alt="Screenshot 2025-11-27 081133" src="https://github.com/user-attachments/assets/3b8d33ee-3ec0-454a-acc5-a80325043df5" /># -Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib-

__Aim:__

To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.

__Apparatus Required:__ 

1. Software: Python with NumPy and Matplotlib libraries
   
2. Hardware: Personal Computer

 
__Theory:__

Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its 
frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier 
wave is varied according to the instantaneous amplitude of the message signal.

__Algorithm:__

1. Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and 
   frequency deviation.
   
2. Generate Time Axis: Create a time vector for the signal duration.
    
3. Generate Message Signal: Define the message signal as a cosine wave.
    
4. Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.
    
5. Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.
 
6. Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

__Programme:__
```
import numpy as np
import matplotlib.pyplot as plt

# Parameters
Am = 41.3         # Message amplitude
Ac = 82.6         # Carrier amplitude
fm = 460          # Message frequency
fc = 920          # Carrier frequency
kf = 200          # Frequency sensitivity
fs = 200000       # Sampling frequency (high for smooth FM)
t = np.arange(0, 0.01, 1/fs)

# Message Signal
message = Am * np.cos(2 * np.pi * fm * t)

# Carrier Signal
carrier = Ac * np.cos(2 * np.pi * fc * t)

# FM Modulated Signal (correct formula)
beta = (kf * Am) / fm
fm_signal = Ac * np.cos(2*np.pi*fc*t + beta * np.sin(2*np.pi*fm*t))

# FM Demodulation (Differentiate + Envelope)
temp = np.diff(fm_signal)            # differentiate
demodulated = np.abs(temp)           # envelope
t2 = t[:-1]                           # time adjust

# Plotting
plt.figure(figsize=(12,10))

plt.subplot(4,1,1)
plt.plot(t, message)
plt.title("Message Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,2)
plt.plot(t, carrier)
plt.title("Carrier Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,3)
plt.plot(t, fm_signal)
plt.title("FM Modulated Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,4)
plt.plot(t2, demodulated)
plt.title("FM Demodulated Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.tight_layout()
plt.show()
```
Calculation:

<img width="552" height="959" alt="image" src="https://github.com/user-attachments/assets/ea13a5d8-c287-410a-bb3f-8f7ba7a9c0b9" />

table:



__Output:__
<img width="890" height="1021" alt="image" src="https://github.com/user-attachments/assets/62952244-5b29-492e-bb2a-3511ba1fb19e" />



__Result:__

<img width="452" height="940" alt="Screenshot 2025-11-27 081228" src="https://github.com/user-attachments/assets/1a443460-f661-42a9-bd08-139d77d0ae3f" />
