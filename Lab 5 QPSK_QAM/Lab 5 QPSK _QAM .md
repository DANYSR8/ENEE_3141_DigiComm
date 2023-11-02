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
This blocks takes two signals and multpily them together and output the product of the two withe an aproximate scale factor of 1  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9ab71280-caf1-4597-807d-710db841e157)


## QPSK Theory  

Quadrature Phase Shift Keying (QPSK) is a digital modulation method that represents binary data using four distinct phase states: 0, 90, 180, and 270 degrees. Each phase state corresponds to a unique pair of binary bits, allowing two bits to be transmitted per symbol. This allows QPSK  to be bandwidth efficent.

### QPSK Modulation 
#### Block Diagram Representation 

The overall block diagram displays the end goal for this section. It displays the complete generation of a QPSK signal, going from a digtal signal that is split up the data from odd and even bits, where each is multiply by a basis fucntion, either a sine or cosine. Each signal is then added together giving the overall QPSK singal that will be transimited.

![Overall 4 ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/284c3d63-90b1-4f60-b6c9-7dbf5490b1c3)


#### Lab Equipment QPSK Modulation Results 

This first figure displays the digtial message that was split into two binary message which can be see in the blue and orange waveforms 

![PART 1](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f32bb8a9-2345-4a57-9d7a-6d3736e341a9)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4c74f640-e8f2-4ef5-abc6-f0ab43a6f0c7)

This second block displays one of the two split digtial signal being multpying by a baisis function. When probing one of outputs of the multplier block we see the bluewave form, that looks like a plain sinisol wave but with aburt changes in phase. These are the transitions points of the digital singal where it change from 1 to 0 or vice versa. To help distisuhing the signals these two outputs of the multpiy block the signals are denoted as PSK <sub>I</sub> and PSK <sub>Q</sub> 


![PART 2/3](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9aa44fab-a485-4614-bd77-df036cdd08ef)
![Part 2 Result](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/806d6dba-459f-4d2f-ac4b-c214301dc7ec)

Finally when the two PSK <sub>I</sub> and PSK <sub>Q</sub> signals are added together we get the final QPSK singal that is ready to be transmitted. This signal has encoded the set digtial symbols using phase, which is ultimely due to the use of the orthangonal baisis functions of sine and cosine to help encode the symbols of the message. 

![part 3 Reslts ](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/c665a52e-56d0-46e6-806b-02a323befd06)


#### QPSK Modulation Discusion 


### QPSK Demodulation 
#### Block Diagram Represenation 

Our Emona kit could not demodiulate the whole signal and recover both PSK <sub>I</sub> and PSK <sub>Q</sub>, due to the amount if modules aviable on the kit, but the kit is capable to recover just one of the PSK signals. This is what the figure below displays,  how we would need to multply by a known carrier signal which is called the "lost carrier"  and then use our filtering techiques to pick out and clean the signals.  

![Overall Part 5](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/661bddf0-5edb-49ca-94a8-67858e656c27)


#### Lab Equipment QPSK Demodulation Results 

The three pictures below display how when trying to revocer the singal the phase of the known "lost carrier" and that carrier can be out of phase of the signal that is trying to be demoudulated. Being out of phases casues these interfences of between the two  PSK <sub>I</sub> and PSK <sub>Q</sub> signals, since the overacrching idea of this modulation techwuie is having these signal being orthogal inorder to pervent such interfences. Hence we used the "Phase Shifter" block to bring the "Lost Carrier" back into phase. Doing so displays the last figure in this section of images were the output of the Lowpass filter more closely matchs the orgial digtial signial displayed in orange. 

![part 4](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e8dce75c-7cc3-4048-94bd-65c583b2dcf1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f4d964b1-4a6e-4851-8130-6b7381edcaa4)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9ff5a39c-5007-4a59-95dd-ec85baa2709d)

Although the pvricous figures displays a somewhat clear digtial signal being recover if any nose where to be present the waveform could become diffucity to uderstand. So to help prevent that and clean up the signal a compartor can be used to minimze this. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/561ccbb7-9d75-4b95-88cf-0ebb00be2933)


We can also see how supsectiple a QPSK signal is to noise, by using the channel module to simulate the signal traveling through the air being interpcept by noise. Below are the signals recovered from being introducted to nosie with each figure increasing the amount of noise introdueced. 

![20](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3f06471a-6efa-490b-91e9-574f4ead69b2)
![6](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/106981f4-f92a-4350-8f9a-7485ebc5216e)
![0](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d155791e-5aa6-4bdd-8077-dace89e5f13c)

Ultimeltey it can be seen that even with nosie being introduce it is possible to still make out some of the main constellation points. 

#### QPSK  Demodulation Discusions



## QAM Theory 

Quadrature Amplitude Modulation (QAM) is a modulation method that efficiently encodes digital data for transmission. It combines amplitude and phase variations to represent digital symbols. In a constellation diagram, each point corresponds to a unique combination of amplitude and phase, representing specific bit sequences. Overall QAM is bandwidth-efficient tecnhuie that is widly used and in enese fundemntal to modern communications. 

### QAM Modulation 
#### QAM Modulation Block Representation 

The overall block digram below displays a simlar method to QPSK where the and I and Q messages are being mulptliy by the baisis function which are fundemnetial orthogranl to each other, which are then added toghter to form the QAM signal that would be tranmitted. In this case our I and Q messages are analog sinisoial waves.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ea5e8d8c-ce1f-43e3-9965-7e8081e9ff0e)


#### Lab Equiment QAM Modulation Results  

The figures below illustrate the outputs of each multiplication block. In the first figure, you'll find the 1kHz sine wave in orange, along with the multiplication of the 100kHz cosine and 1kHz sine waveforms, showcased in blue. The second figure presents the 2kHz signal in blue, accompanied by the product of the 2kHz sine wave and the 100kHz carrier signal, beautifully displayed in orange.

![Part 1](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/82e79a2d-17ec-49b0-aba4-d8bab9d6a0af)
![1kHz](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ec335874-3a90-4bc2-af1b-fd7391361d0f)

![Part 2](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5e077cb6-bfc6-49f5-b099-849e6f3187d5)
![2kHz](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/560320df-3890-4e3d-904a-e754acbef986)


When the two signals above are added together, the resulting waveform is the one displayed below, which essentially represents the QAM signal to be transmitted

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ea5e8d8c-ce1f-43e3-9965-7e8081e9ff0e)
![Addition](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/035af735-2800-48a8-a319-7da460c763c8)


#### QAM Modulation Discusions


### QAM Demodulation
#### QAM Demodulation Block Representation 

As with the QPSK demoultaion, we cannot recover both I and Q singals at the same time therfore we apply the same discrimnation method can be applyed to tune in to one of the individual I or Q signals. Employing the a phase shifter along with multpliy it by the "lost carrier" in order to tune into the corrsponding I and Q signals. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/44dc509c-26c4-4517-a3e2-3ff81a49618d)


#### Lab Equiment QAM Demodulation Results  

![Part 3](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d83c770e-ace4-4cdb-b9cb-f797dc862220)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/611736c0-2df8-41cb-a24f-89fc005c37f6)


![Part 4](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/aba58fa1-4f9a-445c-af18-bd97bd9b3232)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b5333441-5a7c-4f4a-a67a-87be29021896)

![Part 5](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2c136450-74a5-460f-9310-c02da9fdb2b9)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8778f707-246a-42df-8ff7-692d4e6b2db5)


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/91076ab9-d2ab-45a8-a72e-ff332b717cac)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5d28e4ec-e1d2-46aa-8bf0-464ce9436c52)


#### QAM Demodulation Discusions
