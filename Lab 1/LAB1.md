# LAB 1 AM Modulation & Radio

## Objective of the Lab 
This lab aim to accomplish the following using GNURadio Software and SDR Radio Reciver Kit: 

+ Build an AM Radio 
+ Abillty to tune to differnet radio staions
+ Contain a visual graphical user interface (GUI)
+ GUI contains Fast Fourier Transform (FFT) and waterfall visual representation

## Overall Flow Block Diagram of AM Radio 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/de5b59ed-4711-4832-b04f-6e5d05ca4ef0)

## Flow Block Diagrams Explanation 
### Project Setup and Variable Declaration 
These few block contains the setup of the project file as well as the variables used in the AM Radio. Speciccly the GUI Range blocks are
specficlly useful for having user inputs that can be changed while running the the programs. All that is need is to have the start, stop, and step
size of the variable that we wish to adjust while in the program. 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f6535e33-9a67-48fe-9a82-d457f2e63acd)

Additionally the two blocks below are used to set up the project aswell, the "throttle" block ensures that device running the project does not over work the CPU, 
actting as a seftey net. As for the the "Audio Sink" it simply connects the project to the device's speaker as long as the correct frequency is inputed into the block.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/169d9c64-f594-45ea-a7b8-f69b61c7c336)


### Signal Receiving 
Since the overall lab is asking to create a AM radio that receives the corresponding signals. Just like any other signals, AM uses carrier signals in order to
transmist the infomation long distances without having to use nearly as much power. Recovering these AM signals can be done "product demodulation" which is taking the transmitted signal and multiplying 
it by the a sine wave with the same carrier frequency. This will demodulate the transmitted signal to the original information but will still contain nosie. The block below shows the GUI Range varible that is 
used in the product demodulation as "Ch0" frequency".    

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/02efbce8-c3f1-4f22-a4fb-f9f4482b438f)

### Frequency Filter 
After using product demodulation the whole signal is still now avaliable to be heard, but this means all frequency will be heard at the same time which will make the signal be hard to listen or overall inaudiable.
Therefore a low pass filter is used to take out the frequecys we want to hear which in this case is anything below 5kHz. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/92826523-d991-4b1d-bc1d-0881ef160b13)

### AM Demod
Even after filtering the signal with a lowpass filter, the signal still contains unwated noise that will be pass through the low pass filter. Since the an ideal low pass filter would be a "brick wall " filter  which would be a filter that cutoff directly at the specific cutoff point. But in reality it ramps down and surpass the cutoff point. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/23fda64b-88a5-4bec-bbaf-88be2df2b245)

Idea Brick Wall Low Pass Filter VS Typical Response

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d551e4a9-063f-4699-9ce2-ac48536ac715)

### Rational Resampler 
This last fucntional block is a "rational resampler" which is used to match the frequency between two block, since if the incomming signal is running/sampling at a frequecy greater than the reciving device the diffence between the two will "chop up" the signal. For example our incoming signal was being sampled at 400kHz but our speakers was being sampled at 32kHz, therefore the resampler matches the frequencys of the speaker by Decimation ( which reduces the sample rate) and Interpolation (which increases the sample rate). In general this resample is done by multpliy and or dividing by a certin constants. In our case we divided by 400kHz and followed it up by multiplying by 32kHz. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bc2bee30-626c-460c-871a-6141247523c9)



### GUI Blocks 
These blocks serve as the visual elements taht will be displayed on the graphical user interface (GUI). It this case we used a "Frequency Sink" which displays the fast fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moiving down such as a waterfall, frequency on the horizontal axis and the magnetude of the specific frequecy displayed as diffennt shades of color as to show its intensity.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)

## Working GUI & AM Radio 
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to it values. As for the graphs below you can see the waterfall display showing the intensity of the current frequecy range , and the frequency sink displaying the FFT of the incomming signals.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3c564670-a2d1-44c5-b894-1450f1449abb)

