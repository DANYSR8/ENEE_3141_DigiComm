# Lab 4 Emmona Telecomuncations Application 

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


## ASK Modulation & Demodulation 
### ASK Modulation 
#### Block Diagram Representation 
TEXT HERE 

![ASK Modulatiom Blocks](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4b1da712-1979-4876-aefa-f9a67c899f4c)

#### Emona Modulation Online Results 

TEXT HERE 

![No VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/fa4be9d9-5e4b-4aea-a4e0-08d235cce9c1)
![With VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f3345da5-2249-4555-ab29-38a8bb413f9b)


### ASK Demodulation 
#### Block Diagram Represenation 
TEXT HERE 

![ASK Demodulation Blocks](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/81019f43-cf4d-469f-95fb-3accf57f6253)


#### Emona Demodulation Online Results 

Text Here 

![No Comparator Low FC](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9321bcee-4549-4508-bd1c-fd29fa2c0d40)
![No Comparator HIGH FC](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3ef52ab3-e435-4885-8153-4bbedb27acb7)
![With Comparator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e24fcf7f-0537-43bd-ab57-2224e0bd763a)


#### ASK with Noise Block Diagram Representation 

TEXT HERE

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/16a19815-df10-4f79-a10f-fa459e5f67d3)

#### Emona Demodulation with Nosie Online Results 

TEXT HERE 

![Nosie Added before Rectifier](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d4498158-fd44-40d3-aa55-ecd66c829e32)


## FSK Modulation & Demodulation 
### FSK Modulation 
#### FSK Modulation Block Representation 

TEXT HERE 

![FSK Blcoks Modulation ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5609058d-0dae-43da-90ca-87f744bfd5bb)

#### Lab Equiment FSK Modulation Results  

TEXT HERE

![FSK generation](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f1835708-63bd-4219-ada7-235088aeae31)


### FSK Demodulation
#### FSK Demodulation Block Representation 

TEXT HERE

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ebdea8f9-ec12-4514-8a28-63b9c330371e)\


#### Lab Equiment FSK Modulation Results  

TEXT HERE 
![Low Pass Filter Output](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/19add0c9-77de-4d13-92a3-72a200bd6f08)
![Recifier output](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/a3139692-9c0f-486d-8a13-ecd10c586c47)
![Comparator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e2ac4e16-fb13-453c-823d-3b780de75b36)





