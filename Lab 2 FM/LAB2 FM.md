# LAB 1 AM Modulation & Radio

## Objective of the Lab 
This lab aim to accomplish the following using GNURadio Software and SDR Radio Reciver Kit: 

+ Build an AM Radio 
+ Abillty to tune to differnet radio staions
+ Contain a visual graphical user interface (GUI)
+ GUI contains Fast Fourier Transform (FFT) and waterfall visual representation

## Overall Flow Block Diagram of AM Radio 
![Overall Flow Diagram ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/a28ff324-1bdb-441d-999b-6d31753da57b)


## Flow Block Diagrams Explanation 
### Project Setup and Variable Declaration 
These few blocks contain the setup of the project file as well as the variables used in the AM Radio. Specially the GUI Range blocks are
specifically useful for having user inputs that can be changed while running the the programs. All that is needed is to have the start, stop, and step size of the variable that we wish to adjust while in the program.

![Project Setup](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f6535e33-9a67-48fe-9a82-d457f2e63acd)

Additionally, the two blocks below are used to set up the project as well, the "throttle" block ensures that the device running the project does not overwork the CPU, acting as a safety net. As for the "Audio Sink," it simply connects the project to the device's speaker as long as the correct frequency is input into the block.

![Throttle Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)
![Audio Sink Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/169d9c64-f594-45ea-a7b8-f69b61c7c336)


### Signal Receiving 
The overall lab is asking to create an AM radio that receives the corresponding signals. Just like any other signal, AM uses carrier signals in order to transmit the information long distances without having to use nearly as much power. Recovering these AM signals can be done by "product demodulation" which is taking the transmitted signal and multiplying it by the sine wave with the same carrier frequency. This will demodulate the transmitted signal to the original information but will still contain noise. The block below shows the GUI Range variable that is 
used in the product demodulation as "Ch0" frequency".   

![RTL SDR Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/02efbce8-c3f1-4f22-a4fb-f9f4482b438f)

### Frequency Filter 
After using product demodulation the whole signal is still now available to be heard, but this means all frequencies will be heard at the same time which will make the signal be hard to listen to or overall inaudible.
Therefore a low pass filter is used to take out the frequencies we want to hear which in this case is anything below 5kHz. 

![Low Pass Filter](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/92826523-d991-4b1d-bc1d-0881ef160b13)

### AM Demod
Even after filtering the signal with a lowpass filter, the signal still contains unwanted noise that will be passed through the low-pass filter. Since the an ideal low pass filter would be a "brick wall " filter which would be a filter that cuts off directly at the specific cutoff point. But in reality, it ramps down and surpasses the cutoff point. 

![AM Demod](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/23fda64b-88a5-4bec-bbaf-88be2df2b245)

![Idea Brick Wall Low Pass Filter VS Typical Response](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d551e4a9-063f-4699-9ce2-ac48536ac715)

### Rational Resampler 
This last functional block is a "rational resampler" which is used to match the frequency between two blocks, since if the incoming signal is running/sampling at a frequency greater than the receiving device the difference between the two will "chop up" the signal. For example, our incoming signal was being sampled at 400kHz but our speakers were being sampled at 32kHz, therefore the resampler matches the frequencies of the speaker by Decimation ( which reduces the sample rate) and Interpolation (which increases the sample rate). In general, this resampling is done by multiplying and or dividing by certain constants. In our case, we divided by 400kHz and followed it up by multiplying by 32kHz.

![Resampler](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bc2bee30-626c-460c-871a-6141247523c9)



### GUI Blocks 
These blocks serve as the visual elements that will be displayed on the graphical user interface (GUI).In this case, we used a "Frequency Sink" which displays the fast Fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moving down such as a waterfall, frequency on the horizontal axis, and the magnitude of the specific frequency displayed as different shades of color to show its intensity.

![Waterfall Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![Frequency Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)

## Working GUI & AM Radio 
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to its values. As for the graphs below you can see the waterfall display showing the intensity of the current frequency range, and the frequency sink displaying the FFT of the incoming signals.    

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ac6e1b5d-71ec-4cf5-a4fa-30a28f6af287)

