IDEAL SAMPLING
# Aim:
The aim of ideal sampling is to take a continuous-time signal and convert it into a discrete-time signal in such a way that the original signal can be perfectly reconstructed from the samples. This process is governed by the Nyquist-Shannon Sampling Theorem, which states that the sampling rate must be at least twice the maximum frequency component of the signal to avoid aliasing and ensure accurate reconstruction

# Tools Required:
Signal Generator:

A tool to generate the continuous signal (e.g., sine wave, square wave, etc.) to be sampled.

Sampling System:

Analog-to-Digital Converter (ADC): To convert the continuous-time signal into discrete samples.

Software for Simulation and Analysis:

MATLAB or Python (with libraries like NumPy, SciPy, Matplotlib): These are essential tools for simulating the sampling process and analyzing the results. In Python, you can use libraries like NumPy for numerical operations and Matplotlib for plotting the waveform.

Oscilloscope: To visually inspect the signals (if working in a physical setup).

Reconstruction System (optional but useful):

Digital-to-Analog Converter (DAC): To reconstruct the continuous signal from the samples.

# program:
#Impulse Sampling
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample
fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()

# Output:

![download](https://github.com/user-attachments/assets/b9d59983-d17e-417e-9139-3d8ece9b9f5e)
![download (1)](https://github.com/user-attachments/assets/41d2edea-dd72-4577-95b4-6a930cbd9d0c)
![download (2)](https://github.com/user-attachments/assets/d8022470-1e0c-4147-94ff-476ed9f90c21)




# Result:
The output will be a plot showing:

Continuous Signal: A smooth sine wave representing the original signal.

Sampled Points: Red dots (or vertical lines with markers) indicating the discrete samples taken at specific time intervals.

