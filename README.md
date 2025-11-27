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
Am = 41.4       # Message amplitude
Ac = 82.8       # Carrier amplitude
fm = 470        # Message frequency
fc = 4700       # Carrier frequency
kf = 200        # Frequency sensitivity

fs = 200000     # Sampling frequency
t = np.arange(0, 0.01, 1/fs)

# Message Signal
message = Am * np.cos(2 * np.pi * fm * t)

# Carrier Signal
carrier = Ac * np.cos(2 * np.pi * fc * t)

# FM Modulated Signal
beta = (kf * Am) / fm
fm_signal = Ac * np.cos(2*np.pi*fc*t + beta * np.sin(2*np.pi*fm*t))

# FM Demodulation (Differentiate + Envelope)
temp = np.diff(fm_signal)        # differentiate
demodulated = np.abs(temp)       # envelope
t2 = t[:-1]                      # match time length

# Plotting
plt.figure(figsize=(12, 10))

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
__Output:__
<img width="1189" height="990" alt="image" src="https://github.com/user-attachments/assets/9a64e424-7855-40a6-8adc-0e4e8a470469" />

__Result:__
<img width="1280" height="387" alt="image" src="https://github.com/user-attachments/assets/2aed1c5c-907d-4980-a3cb-683a9391ccdc" />

