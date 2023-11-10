# Lab 6 Emmona Telecomuncations BER and SNR

## Introduction 
This lab aims to take the concepts of SNR and BER modulation and applying them to an Emona 101/C Telecommuncations Experimenter. This device is an Hands-On Modern Analog & Digital Telecomuunication Devices that contains a vareity of moduldule than can be used to modulated and demodulates signals. The overall device that can be seen below, is an educational tool that is used to teach students learn about communcations and telecommunication principles, with out havig tools be confuser or held down with some of the more complicated mathmaitical princples. In essence this device creates an layer of abstraction helpful in breaking down the concepts.    

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/93b115e8-e2ff-4734-a4a3-a36fa6de4f08)


## Block Diagrams Explanation 
### Master Signals
This block contains a set of analog and digital singals that can be use for simulated messages and carriers. This block is mainily used as a signal source. 

![Master Signal](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/72ee4537-53af-4636-a9b0-335e67d667c0)

### Sequence Generator
This block outputs two sets of digtial singal label X and Y, the block also contains a SYNC output that sends a pulse at the beigning of  the "X" signal transmition. Additionaly this block requires an external clock in order to function.

![Sequence Generator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d411061d-7cfa-4906-922f-3ca27eaa9ed2)

### Dual Analog Switch
This block functions as a normal switch that is controled by a digital singal, when this switch is closed it allows both possible inputs to go through. Viceversa when the switch is open.

![Dual Analog Switch](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b0ca2c8c-b824-418c-8206-2d24ef2acda7)

### VCO
This block serves as a variable frequicey output source allowing to be used as an iput signal for the system, that can change its frequency on the fly.

![VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/89332d1d-4199-40e8-a4bf-342553fe2732)

### Utilities
The Rectifier Block is a half wave recitftier, which takes in an analog signal and blocks any negative part of the signal leaving only the postive portion of the wave left.

![Rectifier](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/c02913be-fe98-4fad-be28-bf207ffc1283)

The Comparator Block acts as a Schmitt Trigger, where a refence ponit is fed in into the compartator along with the transmitting singnal. This when compares the signal with the refence point. If the singal is greater that the refrence cutoff the block will output an digtial logic of 1 , if the signal is below the refreence it outputs an digtial logic 0. This process helps in clenaing the signal and creating distcetd 1's and 0's that can be transmitted. 

![Comparator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/192e8988-532c-49c7-8342-78d1f2b2d23a)

### Tunable LPF
This block serves as a Low Pass Filter that can varriy its cutoff frequecy. 

![Tunable Low Pass Filter](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/47237533-bf62-421b-8bbe-269103e0e846)

### Nosie Generator 
This block provides 0dB, -6dB, and -20dB amplitudes of electrical nosie that are use to simulate distrubulances that are encounter in signal telecomuncation 

![Noise Generator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/032b3294-e3bf-4bc9-b999-64fec32bc5e6)

### Variable DCV 
This block serves as a variable DC input and can be adjusted from -2.5V to 2.5V.

![Function Generator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b6cd17f3-d980-419a-95f3-83d4987669a0)

### Adder 
This block adds two signal together, the moudule also contains two gain coefficent that are mutltipy two thier respective input signal. The overall equation the module follows is Output = G*A + g*B.  

![Adder](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2876aee6-a59b-4b77-9f52-f67fabe023c7)

### Channel Module 
This block simulates a signal traversing a wire or cable channel, such as a telephone. This block has a frequency cutoff at 2kHz as well.  

![Bandpass Filter](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b29bc666-22db-4e4e-b60f-30f5bb3eea93)

### Phase Shifter 
This block performs a phase shift which is a delay in time between the input and output. This block allows the user to determine the amount of phase shifting.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/30e230c7-14d0-4fde-953e-7123101de01f)


### Serial to Parallel Converter 
This blocks takes in serial dits and brekas them into two parrallel data being trasnmit at the same time, In esence the block splits the streams of 1's and 0's, dividing the stream into odd and even bits. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9603b1fd-60cf-4b18-82ba-8cd7a4a6f4cf)


### RC Low Pass Filter 
This block is a fixed low pass filter comprised of an resitor and capacitor, blocking higher frequency signals approxamitly around 2kHz 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/728ce720-33fe-4d83-9d6e-24720215ad7f)


### Multiplyer 
This blocks takes two signals and multpily them together and output the product of the two withe an aproximate scale factor of 1  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9ab71280-caf1-4597-807d-710db841e157)


## SNR
### SNR Theory 

Signal-to-Noise Ratio (SNR) is a fundamental concept in communication systems, representing the ratio of the signal strength to the background noise level. It quantifies the quality and reliability of a signal by comparing the power of the transmitted signal to the power of any interference or noise present. A higher SNR indicates a cleaner and more reliable signal, making it easier for receivers to distinguish the intended information from unwanted disturbances.

### SNR Block Diagram Representation 

The two figures below display the setup used to generate a digital signal that would encounter noise. While the first block diagram displays the digital signal experiencing all the noise, the second displays the use of a Baseband Low Pass filter filtering out the higher frequencies of the noise.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bdbee5a8-dcc1-49f5-ab48-372029fd9e00)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7d640183-367d-4701-85de-7a8073eca9b2)

### Emona Online Results 
#### Adding Noise to Signal 

The figures below display increasing amounts of noise that the digital signal is exposed to, starting from 20dB and working its way down to 0dB, where essentially the noise is at the same magnitude level as the signal. It can be seen that the digital signal becomes unrecognizable quickly when introducing a huge amount of noise.

Noise 20dB Digital Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e0eda81f-ecb5-4bd7-bf9b-6910eae0246e)

Nosie 6dB Digitial Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/fa6c7d69-0a29-433a-8c43-7b18fe406d76)

Nosie 0dB Digitial Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/96102718-6f78-48bc-b996-1044986a686a)


#### Band-Limiting the Nosiy Signal 

The figures below follow the same setup as before, but in this case, a Baseband Low Pass filter was implemented to limit the amount of noise seen by the signal and, in short, maintain the original signal. However, we can observe that as more noise is introduced to the signal, the filter will attempt its best to maintain the original signal but will eventually lead to the flat section of the digital signal becoming wavy and varying in amplitude. This effect is evident in the figure with a 0dB.

Noise 20dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/57ca459d-5bac-47c9-a84f-59e2a3f5c3ff)

Noise 6dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b8cf0be9-bfa7-49a3-9d0c-e83a6b5f7276)

Noise 0dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/287feee3-35e3-44de-88b8-e764b90f7746)


#### Determining SNR 

The table below was compiled by measuring the RMS voltage values of the corresponding signal. Each signal was measured individually while the other was disconnected from the adder. The obtained values were then substituted into the equation seen below to calculate their Signal-to-Noise Ratio (SNR) in both ratio and logarithmic forms.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3df5475a-2104-4b21-bbb9-0aa2c1638e0c)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3f04b160-dc94-4533-860a-9d8e856d3b2c)

As for calculating the SNR using the alternative method, the equation below was implemented, and the entirety of the data collected can be seen in the table below as well.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2bf67b97-3696-4346-b7ab-31345bd727d1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ac1331f3-5824-4fd5-8d4f-4749a88ff0fe)


#### Eye Diagrams 

![20dB VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/84d17e8f-363d-4567-b7c6-0ad0e4956e3e)

![6dB VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6e0c9ca7-811a-4d11-94ef-25cdd6668c83)

![0dB VCO ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e8370ef2-3985-4049-bdaa-aad902e07e78)


![lower VCO Fre ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/13836f31-0a23-4ebb-8f72-f31bba014f90)

![High VCO Fre ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/73770fd6-a321-421f-96c2-29245e528c14)


### SNR Discusion 

The noise generator module seems to be modeling white Gaussian noise, where the amount of noise increases as the dB value decreases. In a sense, a 20dB value implies that the noise is 75% smaller than the magnitude of the original incoming signal, and a 0dB value means the noise and signal have the same magnitude compared to each other. The actual Signal-to-Noise Ratio (SNR) tells us how many times the signal is stronger than the noise, providing a direct scalar factor. Even though we calculated the SNR using two different methods, they produced similar results due to the fact that we are measuring the difference between signal and noise, which is something that cannot be characteristically changed regardless of how you calculate the SNR. In doing so, we can expect the SNR to decrease as the noise increases, since the SNR indicates the difference in signal magnitude compared to the noise magnitude. Therefore, the lower this value, the more prevalent the noise is in the transmission of the signal.  

## BER
### BER Theory 
The concept of Bit Error Rate (BER) is fundamental in digital communication systems. BER quantifies the accuracy of transmitted data by measuring the ratio of received bits with errors to the total number of transmitted bits. A lower BER indicates a higher quality of communication, reflecting the system's ability to transmit data accurately


### Lab Equipment BER
#### Characterrising Bandpass Low Pass Filter Frequnecy Response 

The figures below display experimental data collected to determine the characteristics and specifications of the Bandpass Filter. This was achieved by adjusting the frequency of a constant magnitude AC signal, recording the filter's output, and plotting the results. The last figure in this section displays a feature that our oscilloscope contains, where the above process was done automatically

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/76333317-e4fc-40a6-926c-e079f5f39e9d)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7c976a8a-5726-4113-be7e-eee33f0c3d37)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7cd75f84-4ff2-48f8-9755-353cdebd3c53)

### Block Diagram Representation 

The block diagram below illustrates the overall connection used in setting up a signal and noise composite that will travel through a baseband channel. It ensures it's a digital signal that is being added by noise, which can be controlled and given a DC offset

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/93e81fa8-f09e-4218-8ff4-d751a027019e)


#### Signal and Nosie Componets of Baseband 

This section presents the results gathered and how Signal-to-Noise Ratio (SNR)has an impact on Bit Error Rate (BER). The images illustrate the digital signal represented by an orange waveform and the noise depicted by a blue waveform. Furthermore, the corresponding FFT (Fast Fourier Transform) for the frequency cutoff is shown, revealing how it influences the amount of noise introduced to the signal.

High Frequency Cutoff --- > More Noise Present 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/475d2210-1321-4043-8c69-389e6260d8f5)

Lower Frequency Cutoff --- > Less Noise Present 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f649f28b-2668-46fd-be74-a212e0a78810)

The figures below displays the output of the baseband channel, showcasing the combined effects of the signal and noise. The accompanying table presents the measured values, with the first row having a noise level of 0dB and the second row featuring a noise level of 20dB. The final table displays the magnitude measured at a frequency where it is expected that the magnitude will differ by 3dB. However, in this case, we observe a difference of 5dB.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/151cfd41-554e-4026-b8ac-4a48e0dd9004)

![Table](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/94fd6855-768e-478c-b586-c6d096c3816e)

![Table](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/47897e44-7e2b-4862-b903-69724e33a908)


#### Nosiy Signal with Limits 

These set of figures illustrates the setup utilized to measure the occurrence of bit errors. The basic setup involves using a replicated digital signal for comparison with the transmitted signal. If the transmitted signal does not match the replicated signal, an error is recorded. An XOR gate is employed for this purpose; when the two signals match, it outputs a 0, indicating no error. Conversely, a difference triggers a 1, incrementing the error count. This method of checking for bit errors requires that the transmitted signal and the replicated signal be in phase; otherwise, the error counter would consistently report errors for the entire signal.

The figure depicts spikes representing syncing spikes used to align the signals. The initial figure shows the digital signal out of phase, while the second figure illustrates the two signals perfectly in sync. The table ultimately presents the two digital signals in sync, with the only variable being the level of noise introduced to the transmitted signal. The synchronized signal allows us to evaluate how noise contributes to bit errors. Ultimately, our measured results demonstrate that a higher Signal-to-Noise Ratio (SNR) results in fewer bit errors, highlighting the correlation between lower noise levels and enhanced signal integrity.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/cb6700f0-517c-4c60-a15a-424c984939d1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d019c545-5776-49d5-91f7-fa772305f370)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/38f4e207-b4f2-405d-bb89-d4b6c67f174b)


### BER Discusion 

Overall, we determined that the cutoff frequency of the baseband low-pass filter was around 1.5kHz, the same frequency at which the output is approximately 3dB lower than the original. Additionally, the digital data signal appears distorted due to the fact that the low-pass filter is filtering out the harmonics of the square wave in the digital signal. Regarding measuring the bit error rate, we were able to demonstrate that as the signal encounters more noise, bit errors become more prevalent, and vice versa.
