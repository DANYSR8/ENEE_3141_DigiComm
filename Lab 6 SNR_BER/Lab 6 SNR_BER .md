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
### SNR Block Diagram Representation 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bdbee5a8-dcc1-49f5-ab48-372029fd9e00)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7d640183-367d-4701-85de-7a8073eca9b2)

### Emona Online Results 

#### Adding Noise to Signal 

Noiseing 20dB Digital Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e0eda81f-ecb5-4bd7-bf9b-6910eae0246e)

Nosie 6dB Digitial Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/fa6c7d69-0a29-433a-8c43-7b18fe406d76)

Nosie 0dB Digitial Signal 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/96102718-6f78-48bc-b996-1044986a686a)


#### Band-Limiting the Nosiy Signal 


Noiseing 20dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/57ca459d-5bac-47c9-a84f-59e2a3f5c3ff)

Noiseing 6dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b8cf0be9-bfa7-49a3-9d0c-e83a6b5f7276)

Noiseing 0dB Digital Signal with channel low pass 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/287feee3-35e3-44de-88b8-e764b90f7746)


#### Determining SNR 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ac1331f3-5824-4fd5-8d4f-4749a88ff0fe)


#### Eye Diagrams 

![20dB VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/84d17e8f-363d-4567-b7c6-0ad0e4956e3e)

![6dB VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6e0c9ca7-811a-4d11-94ef-25cdd6668c83)

![0dB VCO ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e8370ef2-3985-4049-bdaa-aad902e07e78)


![lower VCO Fre ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/13836f31-0a23-4ebb-8f72-f31bba014f90)

![High VCO Fre ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/73770fd6-a321-421f-96c2-29245e528c14)


### SNR Discusion 


## BER
### Block Diagram Representation 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/93e81fa8-f09e-4218-8ff4-d751a027019e)


### Lab Equipment BER
#### Characterrising Bandpass Low Pass Filter Frequnecy Response 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/76333317-e4fc-40a6-926c-e079f5f39e9d)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7c976a8a-5726-4113-be7e-eee33f0c3d37)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7cd75f84-4ff2-48f8-9755-353cdebd3c53)


#### Signal and Nosie Componets of Baseband 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/475d2210-1321-4043-8c69-389e6260d8f5)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f649f28b-2668-46fd-be74-a212e0a78810)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/151cfd41-554e-4026-b8ac-4a48e0dd9004)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/94fd6855-768e-478c-b586-c6d096c3816e)


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ea4902dd-980a-416d-b277-e4fb5f5938ee)


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/47897e44-7e2b-4862-b903-69724e33a908)


#### Nosiy Signal with Limits 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7178be38-2284-44bc-8152-53188e2b5a3b)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/cb6700f0-517c-4c60-a15a-424c984939d1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d019c545-5776-49d5-91f7-fa772305f370)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6bab85c8-e4c8-49b1-99e4-58d43453c296)


### BER Discusion 

