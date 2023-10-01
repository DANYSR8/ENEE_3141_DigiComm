# LAB 2 FM Modulation & Radio

## Objective of the Lab 
This lab aim to accomplish the following using GNURadio Software and SDR Radio Reciver Kit: 

+ Build an FM Radio 
+ Abillty to tune to differnet radio staions
+ Contain a visual graphical user interface (GUI)
+ GUI contains Fast Fourier Transform (FFT) and waterfall visual representation

## Overall Flow Block Diagram of AM Radio 

![Overall Flow Diagram](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/aea1a788-a73d-4ef6-885f-dedbe7b0d299)



## Flow Block Diagrams Explanation 
### Project Setup and Variable Declaration 
These few blocks contain the setup of the project file as well as the variables used in the FM Radio. Specially the GUI Range blocks are
specifically useful for having user inputs that can be changed while running the the programs. All that is needed is to have the start, stop, and step size of the variable that we wish to adjust while in the program.

![Project Setup](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ef856da1-ba6c-4340-a4e0-4407a896b8d1)


Additionally, the three blocks below are used to set up the project as well, the "throttle" block ensures that the device running the project does not overwork the CPU, acting as a safety net. As for the "Audio Sink," it simply connects the project to the device's speaker as long as the correct frequency is input into the block. Lastly the "multiply constant" block is used to add an additional adjustable varriable which is the volume of the signal.It is essentially takes the final signal before being played by the speakers and boostes it by multiply a scalar value.   

![Throttle Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)
![Audio Sink Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/169d9c64-f594-45ea-a7b8-f69b61c7c336)
![Multiply Constant](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/c42e2599-dba9-4fe3-a46a-726256b1359b)



### Signal Receiving 
The overall lab is asking to create an FM radio that receives the corresponding signals. Just like any other signal, FM uses carrier signals in order to transmit the information long distances without having to use nearly as much power.Recovering these FM signals can be done by "product demodulation" which is taking the transmitted signal and multiplying it by the sine wave with the same carrier frequency.This will demodulate the transmitted signal to the original information but will still contain noise. The block below shows the GUI Range variable used in the product demodulation as "Ch0" frequency" which is the center frquency varible laidout in the setup of the project. The figure also contains a rational resampler that bring sthe "RTL_SDR" block sample rate to the nesseacy 400kHz for the "FM Demod". As a side not the "FM Demod" internally contains a low pass filter which in can be seen by the audio pass and stop values on the block itself.   

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5ba20824-fc71-42c1-b070-c5f84ffbf748)

### FM Demod


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7f113960-6c90-461e-b12b-0853ed6d4bdf)




### Rational Resampler 
This last functional block is a "rational resampler" which is used to match the frequency between two blocks, since if the incoming signal is running/sampling at a frequency greater than the receiving device the difference between the two will "chop up" the signal.The resampler matches the frequencies of the speaker by Decimation ( which reduces the sample rate) and Interpolation (which increases the sample rate). In general, this resampling is done by multiplying and or dividing by certain constants. In our case, we divided by 400kHz and followed it up by multiplying by 48kHz.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ff4c158b-f42c-4115-8e37-5d66f39f3cba)



### GUI Blocks 
These blocks serve as the visual elements that will be displayed on the graphical user interface (GUI).In this case, we used a "Frequency Sink" which displays the fast Fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moving down such as a waterfall, frequency on the horizontal axis, and the magnitude of the specific frequency displayed as different shades of color to show its intensity.

![Waterfall Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![Frequency Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)

## Working GUI & AM Radio 
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to its values. As for the graphs below you can see the waterfall display showing the intensity of the current frequency range, and the frequency sink displaying the FFT of the incoming signals.    

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ac6e1b5d-71ec-4cf5-a4fa-30a28f6af287)

