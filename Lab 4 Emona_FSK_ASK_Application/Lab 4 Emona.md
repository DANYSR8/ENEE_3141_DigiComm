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

The block diagrams below provide a high-level abstraction of how ASK (Amplitude Shift Keying) modulation can be generated. The first block diagram employs a "Master Signal" block, in which a 2kHz sine wave is input to a "Dual Analog Switch" controlled by a "Sequence Generator" block. This configuration simulates an On-Off Keying (OOK) signal, wherein the 2kHz sine wave is allowed to pass through the switch only when the sequence generator outputs a high signal to the "Dual Analog Switch." This ultimately results in a signal representation where a digital 1 is depicted by the sine wave, and a digital 0 is represented by a flat line.  

The second block diagram functions similarly to what was mentioned above. However, in this case, the "VCO" block replaces the input sine wave, enabling users to modify the frequency of the input signal.  

![ASK Modulatiom Blocks](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4b1da712-1979-4876-aefa-f9a67c899f4c)

#### Emona Modulation Online Results 

The figures below illustrate how these block diagrams were implemented using the Emona Online Kits, showcasing the outputs from the probe points in the block diagrams. The red signal represents the start bit, signaling the initiation of the sequence generator's string of bits. The blue signal displays the actual bit sequence provided by the sequence generator. Lastly, the yellow signal represents the 'message,' where the sine wave is allowed to pass through when the blue signal is at a digital logic level of 1. This effectively represents the 0's (spaces) and 1's (marks) of the signal. The Last figure just displayes how the VCO signal can be use to adjust the frequency of the sine wave being let through. 

![No VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2d94c13b-2b3d-4944-b7dc-b5c28981e82a)
![With VCO](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f3345da5-2249-4555-ab29-38a8bb413f9b)


### ASK Demodulation 
#### Block Diagram Represenation 

The block diagrams below present a high-level abstraction of Amplitude Shift Keying (ASK) demodulation. It illustrates how the modulated signal is directed through a rectifier to eliminate the negative wave components, then passed through a low-pass filter to recover a representation of the original signal from the sequence generator.

The first two figures demonstrate that the lower the frequency cutoff of the filter, the less the output signal resembles a digital signal. Conversely, a higher frequency cutoff results in a signal more closely resembling a digital one. To transform this signal into a clear digital form, a comparator, such as a Schmitt Trigger, is employed. The Schmitt Trigger uses two signals: one is the input signal, and the other is a reference signal. If the input signal exceeds the reference, the Schmitt Trigger outputs a digital 1; if the opposite is true, it outputs a digital 0, effectively refining the digital signal. 

![ASK Demodulation Blocks](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/81019f43-cf4d-469f-95fb-3accf57f6253)


#### Emona Demodulation Online Results 

The figures below depict the implementation of these block diagrams using the Emona Online Kits. They highlight the outputs from the probe points within the block diagrams. The order of presentation follows the description provided in the previous section, with a primary focus on the Purple signal (Channel 4), which represents the recovery of the original signal from the modulated carrier.

![No Comparator Low FC](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9321bcee-4549-4508-bd1c-fd29fa2c0d40)
![No Comparator HIGH FC](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3ef52ab3-e435-4885-8153-4bbedb27acb7)
![With Comparator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e24fcf7f-0537-43bd-ab57-2224e0bd763a)


#### ASK with Noise Block Diagram Representation 

The block diagram below illustrates a setup similar to the previous section, with the inclusion of a noise generator integrated into the transmission section of the ASK modulated signal. This noise generator represents real-world interference that the signal may encounter.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/776afb2d-c2a7-497d-813d-025315cf6944)


#### Emona Demodulation with Nosie Online Results 

The figure ultimately illustrates how the noise encountered by the signal can significantly impact the recovery of the transmitted signal, as depicted by the yellow signal (Channel 3). While there remains a semblance of the intended signal, an increase in noise levels would likely hinder the accurate recovery of the signal overall.

![Nosie Added before Rectifier](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d4498158-fd44-40d3-aa55-ecd66c829e32)


## FSK Modulation & Demodulation 
### FSK Modulation 
#### FSK Modulation Block Representation 

The block diagram below illustrates the generation of a Frequency Shift Keying (FSK) modulation signal. The "Sequence Generator" is employed to produce a digital signal that determines when the signal transitions between higher and lower frequencies, effectively distinguishing between marks and spaces. The Voltage-Controlled Oscillator (VCO) regulates this transition by manipulating the frequency of the signal's marks. The higher the frequency of these marks, the greater the distinction between them.

![FSK Blcoks Modulation ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5609058d-0dae-43da-90ca-87f744bfd5bb)

#### Lab Equiment FSK Modulation Results  

We can observe the modulated signal, represented by the blue waveform, and the corresponding digital signal that controls the overall appearance of the modulated signal, depicted in yellow. Additionally, we notice that the frequency spectrum displays two peaks at both of the blue signal's frequencies used to modulate the digital signal.

![FSK generation](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f1835708-63bd-4219-ada7-235088aeae31)


### FSK Demodulation
#### FSK Demodulation Block Representation 

The following block diagrams illustrate the complete process of demodulating the signal. The first diagram demonstrates the isolation of the main frequency, while the second diagram depicts the utilization of a rectifier to eliminate the negative components of the signal. The third and final diagram illustrates the application of a comparator to refine the signal by employing a Schmitt Trigger, as discussed in a manner similar to the ASK Demodulation section mentioned earlier.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ebdea8f9-ec12-4514-8a28-63b9c330371e)\


#### Lab Equiment FSK Modulation Results  

The figures below illustrates each of the steps mentioned previously and their respective outputs corresponding to each step.
 
![Low Pass Filter Output](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/19add0c9-77de-4d13-92a3-72a200bd6f08)
![Recifier output](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/a3139692-9c0f-486d-8a13-ecd10c586c47)
![Comparator](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e2ac4e16-fb13-453c-823d-3b780de75b36)





