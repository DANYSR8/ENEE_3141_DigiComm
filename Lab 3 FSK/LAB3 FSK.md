# LAB 3 FSK Modulation & Radio

## Objective of the Lab 
This lab aim to accomplish the following using GNURadio Software and SDR Radio Reciver Kit: 

+ Build an FSK Transmitter and Reciver 
+ Understand the theroy behind this form of modulatiuon 
+ Contain a visual graphical user interface (GUI)

## FSK Theory 
The overall thery of FSK otherwise known as Frequency Shift Keying (FSK) is a modulation technique that operates on the same principle as Frequency Modulation (FM) but in a digital domian. In FSK, digital data is transmitted by switching between two different carrier frequencies, one representing a low bit (typically denoted as '0') and the other representing a high bit ('1'). The key advantage of using two carriers with distinct frequencies lies in the ease of distinguishing between binary values in the received signal. The difference in frequency between these carriers is referred to as the FSK deviation, or simply frequency deviation. A crucial point to note is that the larger the frequency deviation, the clearer the distinction between individual bits in the transmitted signal. However, there is a trade-off, as a greater frequency deviation requires a wider portion of the frequency spectrum, which can limit the number of FSK signals that can coexist within that spectrum. Below is a time domain representaion of FSK modulation. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5aeed92b-d09c-4853-a76f-9ef87304d398)


## Overall Flow Block Diagram of FM Radio 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f5f9b909-d234-46f9-9cd0-ba63dd0e0302)



## Flow Block Diagrams Explanation 
### Project Setup and Variable Declaration 
These few blocks contain the setup of the project file as well as the variables used in the FSK Transmitter and Receiver. Specially the GUI Range blocks are specifically useful for having user inputs that can be changed while running the the programs. All that is needed is to have the start, stop, and step size of the variable that we wish to adjust while in the program.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8496155f-3457-4c95-8dd3-3a74c9072eec)


Additionally, the three blocks below are used to set up the project as well, the 'repeat' block, for instance, takes the provided input and repeats it a specified number of times, all within the original signal's regular timeframe. You can observe a clear illustration of this in Figure 1, where Signal 1 represents the original signal, and Signal 2 showcases the result of applying a 'repeat' block with a value of 5. As a result, the signal is repeated five times.

1)

![Repeat](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/be0d8e23-c162-495f-89c8-48d3b84aec2b)

![Repeat Example](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4ff6e9e0-3ab3-4d41-b0f4-938408584e13)

2) The "throttle" block ensures that the device running the project does not overwork the CPU, acting as a safety net.

![Throttle Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)

3) As for the "binary slicer" block it simply takes an input signal and if the magnitude of the signal is anything greater than 0 the block will output a 1, else the block with output a 0. Additionally, we add on the "Add Const' block in order to add on a -0.5 to the signal in order to make it easier for the binary slicer to determine whether the signal should be 0 or 1 (acting as a DC offset for the signal).    

![Binary Slicer](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4e20f397-5153-489c-9146-9f8faaaa50f0)

Lastly the "Uchar to Float" block converts the singal from a unsigned character into a float to be used later down the flow diagram.  

### GUI Blocks - The Visual Elements  
These blocks serve as the visual elements that will be displayed on the graphical user interface (GUI).In this case, we used a "Frequency Sink" which displays the fast Fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moving down such as a waterfall, frequency on the horizontal axis, and the magnitude of the specific frequency displayed as different shades of color to show its intensity. And lastly, the time sink displays the signal in the time domain, which is useful in visualizing the signals in a domain most people are accustomed to.

![Waterfall Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![Frequency Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)
![Time Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/04ea58e7-dfff-45c8-a248-4a9e3e0a96d7)



### Signal Transmitting 
The entire flow diagram is broken down into two sections, FSK transmitter and FSK receiver. The section below displays the transmitter section where the vector source (otherwise known as the message we wish to transmit) is fed into a "frequency mod " block which as the name applies modulates the input to a frequency-modulated output. To be more specific GnuRadio states " This block is an input amplitude controlled complex sine. It outputs a signal, which has a momentary phase increase that is proportional to the sensitivity and input amplitude. More specifically, takes a real, baseband signal (x_m[n]) and outputs a frequency-modulated signal (y[n]) according to the equations below.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3e11c3e5-048b-4742-bcf4-047eaf29b39f)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e79d747c-0378-43fc-b100-7bdfc06c61ab)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8ddf3bd1-c784-40c5-b7cb-6e5c91ce1fe4)

Once the vector source is modulated it is then multiplied by a carrier signal which in this case is a Cosine with a frequency of 2 MHz, this will ultimately give us our FSK modulated signal to be transmitted. This transmitted signal can be seen below as well as the labeled corresponding bits of the original source.
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/773d0bb8-8f60-4641-b2ac-86e77f53451c)



### Signal Receiving 
This section of the flow diagram displays the FSK receiver, where the signal from the "Signal Transmitting" section is taken and filtered, demodulated, and ultimately fed into the binary slicer to determine its value,  below the block diagrams the figures display each step of the flow diagram showing how each step makes the signal clearer eventually getting to a clear binary form.

![RX section](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ca216563-84bf-4ce9-8d43-6c7092ed06c3)

![FIR Filter Out](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/05587996-51b4-4f3c-9f3d-697d0b88e186)

![Demod Out](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bfce5d49-9f3b-466b-a5a9-6196c20bc698)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/2346310d-16d0-452f-b3ff-b59eeb12a5fc)




## Working GUI & FSK Reciverer and Transmiter  
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to its values in this case the FSK deviation variable. The variety of figures below displays different binary messages that were sent through this flow diagram and shows how the messages were being sent and received.  

#### Vector Source (-1,1) 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/05354ecd-4868-48e7-be3b-775ec43b124e)

#### Vector Source (-1,-1,-1,-1, 1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/989fd9b1-22d0-4b2e-9cbe-993da127094d)


#### Vector Source (1,1,1,1, -1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/39cf01f6-7c9e-4a5c-a73e-6656591dcfc2)

#### Vector Source (1,-1,1,-1, 1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ee5c38fd-1ade-44e6-8e32-de512dee45ba)


#### Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/40adf939-77bc-45aa-9b31-08dd239b08da)


As we can see the width of each segment of the final signal corresponds to the amount of repeated values in the binary sequences from the original message. 

#### FSK Deviation 
Additionally, these last two figure displays how a greater FSK deviation allows for easier detection of 1's and 0's but occupy more bandwidth.  

Big FSK Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/5ededf3f-42a8-4b46-8dea-229263214c69)


Small FSK  Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e6f67648-5263-4cf4-9b17-03259988ae3d)


## Uses of FSK

Overall FSK modulation is an essential part of modern wireless communication systems and offers robustness against noise and interference. It is a straightforward modulation technique suitable for transmitting digital data. Whether it's remote control systems, telemetry devices, or data modems, FSK's compatibility with digital data has made it indispensable in the modern tech landscape. In essence, FSK stands as a reliable and efficient modulation technique powering seamless communication in today's digital world. Some possible projects using this technique can be a car keys decoder/repeater, simple RC car controllers, or a wireless data logger, these projects can provide a suitable way of applying this modulation technique




