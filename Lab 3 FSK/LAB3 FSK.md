# LAB 3 FSK Modulation & Radio

## Objective of the Lab 
This lab aim to accomplish the following using GNURadio Software and SDR Radio Reciver Kit: 

+ Build an FSK Transmitter and Reciver 
+ Understand the theroy behind this form of modulatiuon 
+ Contain a visual graphical user interface (GUI)

## FM Theory 
The overall theory behind FSK 

## Overall Flow Block Diagram of FM Radio 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/f5f9b909-d234-46f9-9cd0-ba63dd0e0302)



## Flow Block Diagrams Explanation 
### Project Setup and Variable Declaration 
These few blocks contain the setup of the project file as well as the variables used in the FSK Transmitter and Reciver. Specially the GUI Range blocks are specifically useful for having user inputs that can be changed while running the the programs. All that is needed is to have the start, stop, and step size of the variable that we wish to adjust while in the program.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8496155f-3457-4c95-8dd3-3a74c9072eec)


Additionally, the three blocks below are used to set up the project as well, the " repeat" block simply takes the given input and repeats it a certin amount of times, within the normal time spand of the orgianl singal a clear exapmle can be seen in figure 1. 

1)

![Repeat](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/be0d8e23-c162-495f-89c8-48d3b84aec2b)

![Repeat Example](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4ff6e9e0-3ab3-4d41-b0f4-938408584e13)

2) The "throttle" block ensures that the device running the project does not overwork the CPU, acting as a safety net.

![Throttle Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)

3) As for the "binary slicer" block it simply takes an input signal and if the magnitude of the signal is anything greater that 0 the blcok will output a 1, else the block with output a 0. Additionaly we add on the "Add Const' block in order to add on a -0.5 to the singal in order to make it easier for the bianry slicer to detemine wheather the signal should be 0 or 1 (acting as a DC offset for the signal).  

![Binary Slicer](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4e20f397-5153-489c-9146-9f8faaaa50f0)

Lastly the "Uchar to Float" block converts the singal from a unsigned character into a float to be used later down the flow diagram  




### Signal Transmitting 
The entire flow diagram is broken down into two sections, FSK transmiter and FSK reciver. The section below displays the transmiter section where the the vector source (otherwise known as the message we wish to transmit) is fed into a "frequency mod " block which as the name applies modulates the input to a frequecy modulated output. To be more specific GnuRadio states " This block is an input amplitude controlled complex sine. It outputs a signal, which has a momentary phase increase that is proportional to sensitivity and input amplitude.More specifically, takes a real, baseband signal (x_m[n]) and output a frequency modulated signal (y[n]) according to the equations below.   

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3e11c3e5-048b-4742-bcf4-047eaf29b39f)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/e79d747c-0378-43fc-b100-7bdfc06c61ab)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8ddf3bd1-c784-40c5-b7cb-6e5c91ce1fe4)

Once the vector source is modulated it is then multiply by a carrier signal which in this case is a Cosine with a frequecy of 2 MHz, this will ultimiley give us our FSK modulated signal to be transmited. This transmisted signal can be seen below 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/496a0ea5-f5ca-4833-b57c-ece3e4d69b6f)


### Signal Receiving 
This section of the flow diagram displayes the FSK reciver , where the signal is taken and filted and demodulatioed  and ultimley fed into the binary slicer to determine its value,  below the block diagrams the figures displays each step of the flow diagram showing how each steps makes the signal clearer eventurly getting to a clear binary form.  

![RX section](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ca216563-84bf-4ce9-8d43-6c7092ed06c3)

![FIR Filter Out](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/05587996-51b4-4f3c-9f3d-697d0b88e186)

![Demod Out](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bfce5d49-9f3b-466b-a5a9-6196c20bc698)

![Binary Slicer](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6d6daebd-2a83-4436-832c-58e8836002b4)



### GUI Blocks 
These blocks serve as the visual elements that will be displayed on the graphical user interface (GUI).In this case, we used a "Frequency Sink" which displays the fast Fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moving down such as a waterfall, frequency on the horizontal axis, and the magnitude of the specific frequency displayed as different shades of color to show its intensity. And lastly the time sink displayes the signal in the time domain, which is usful in visulalying the signals in a domain most people are acoustom to. 

![Waterfall Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![Frequency Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)
![Time Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/04ea58e7-dfff-45c8-a248-4a9e3e0a96d7)


## Working GUI & FSK Reciverer and Transmiter  
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to its values in this case the FSK deviation variable. The variey of figures below display differnt binary messages that where sent through this flow diagram and show how the messages were being sent.   

#### Vector Source (-1,1) 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/05354ecd-4868-48e7-be3b-775ec43b124e)

#### Vector Source (-1,-1,-1,-1, 1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/989fd9b1-22d0-4b2e-9cbe-993da127094d)


#### Vector Source (1,1,1,1, -1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/39cf01f6-7c9e-4a5c-a73e-6656591dcfc2)

#### Vector Source (1,-1,1,-1, 1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ee5c38fd-1ade-44e6-8e32-de512dee45ba)


#### Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/1a633756-a66b-4275-9334-4c4b38f45a2f)


#### FSK Deviation 
Additionaly these last two fiugre displays how a greater FSK deviation allows for easier detection of 1's and 0's but occupy more bandwidth 

Big FSK Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ba88a43e-8f46-4a2e-aab1-cd4728574895)

Small FSK  Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/634c0d5f-b5af-4604-8be0-11cf0292df00)


## Uses of FSK
Overall FSK



#### WORK IN PROGRESS 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3514d22f-b6ae-43eb-9500-9d6d3f21f902)

