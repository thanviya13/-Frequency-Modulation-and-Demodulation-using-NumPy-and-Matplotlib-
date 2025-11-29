# -Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib-

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
Tabular coloumn:

<img width="651" height="689" alt="image" src="https://github.com/user-attachments/assets/a7bfa376-2199-44d9-93cd-e364f8972649" />


Calculation:

<img width="470" height="832" alt="image" src="https://github.com/user-attachments/assets/75641850-a7a1-47a9-8c8c-03ba2bf60da4" />


__Output:__

<img width="784" height="590" alt="image" src="https://github.com/user-attachments/assets/a3ccf984-e50f-40af-993c-c1ee0736b1a7" />


__Result:__

<img width="317" height="698" alt="image" src="https://github.com/user-attachments/assets/fe3f72bd-de7f-4fd0-a210-0be415c6d78e" />
