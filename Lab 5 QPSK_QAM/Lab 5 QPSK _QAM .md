# Lab 5 Emmona Telecomuncations QPSK and QAM 

## Introduction 
This lab aims to take the concepts of ASK and FSK modulation and applying them to an Emona 101/C Telecommuncations Experimenter. This device is an Hands-On Modern Analog & Digital Telecomuunication Devices that contains a vareity of moduldule than can be used to modulated and demodulates signals. The overall device that can be seen below, is an educational tool that is used to teach students learn about communcations and telecommunication principles, with out havig tools be confuser or held down with some of the more complicated mathmaitical princples. In essence this device creates an layer of abstraction helpful in breaking down the concepts.    

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
This blocks takes two signals and multpily them together and output the product of the two withe an aproximate scale facot of 1  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9ab71280-caf1-4597-807d-710db841e157)


## QPSK Modulation & Demodulation 
### QPSK Modulation 
#### Block Diagram Representation 

![Overall 4 ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/284c3d63-90b1-4f60-b6c9-7dbf5490b1c3)


#### Lab Equipment QPSK Modulation Results 

![PART 1](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f32bb8a9-2345-4a57-9d7a-6d3736e341a9)


![PART 2/3](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9aa44fab-a485-4614-bd77-df036cdd08ef)


#### QPSK Modulation Discusion 


### QPSK Demodulation 
#### Block Diagram Represenation 

![Overall Part 5](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/661bddf0-5edb-49ca-94a8-67858e656c27)



#### Lab Equipment QPSK Demodulation Results 

![part 4](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e8dce75c-7cc3-4048-94bd-65c583b2dcf1)


#### QPSK  Demodulation Discusions


## QAM Modulation & Demodulation 
### QAM Modulation 
#### QAM Modulation Block Representation 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ea5e8d8c-ce1f-43e3-9965-7e8081e9ff0e)


#### Lab Equiment QAM Modulation Results  

![Part 1](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/82e79a2d-17ec-49b0-aba4-d8bab9d6a0af)

![Part 2](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5e077cb6-bfc6-49f5-b099-849e6f3187d5)


#### QAM Modulation Discusions


### QAM Demodulation
#### QAM Demodulation Block Representation 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/44dc509c-26c4-4517-a3e2-3ff81a49618d)


#### Lab Equiment QAM Demodulation Results  

![Part 3](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d83c770e-ace4-4cdb-b9cb-f797dc862220)

![Part 4](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/aba58fa1-4f9a-445c-af18-bd97bd9b3232)

![Part 5](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2c136450-74a5-460f-9310-c02da9fdb2b9)


#### QAM Demodulation Discusions
