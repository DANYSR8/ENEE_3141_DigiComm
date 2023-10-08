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
These few blocks contain the setup of the project file as well as the variables used in the FM Radio. Specially the GUI Range blocks are specifically useful for having user inputs that can be changed while running the the programs. All that is needed is to have the start, stop, and step size of the variable that we wish to adjust while in the program.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8496155f-3457-4c95-8dd3-3a74c9072eec)


Additionally, the three blocks below are used to set up the project as well, the "throttle" block ensures that the device running the project does not overwork the CPU, acting as a safety net.The "add constant" block is used to add 

![Throttle Block](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9edba9b0-a13d-4500-ad57-c6e7c01fa28b)
![Binary Slicer](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4e20f397-5153-489c-9146-9f8faaaa50f0)
![Repeat](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/be0d8e23-c162-495f-89c8-48d3b84aec2b)

### Signal Transmitting 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/8ddf3bd1-c784-40c5-b7cb-6e5c91ce1fe4)


### Signal Receiving 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ca216563-84bf-4ce9-8d43-6c7092ed06c3)


### Frequency Modulation 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d3e239a1-2f5c-4450-8b7a-cf683c5d3341)



### GUI Blocks 
These blocks serve as the visual elements that will be displayed on the graphical user interface (GUI).In this case, we used a "Frequency Sink" which displays the fast Fourier transform (FFT) of the entire transmitted signal. The "Waterfall Sink" displays time moving down such as a waterfall, frequency on the horizontal axis, and the magnitude of the specific frequency displayed as different shades of color to show its intensity. And lastly the time sink displayes the signal in the time domain, which is usful in visulalying the signals in a domain most people are acoustom to. 

![Waterfall Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/443a98d8-41cd-42c7-8fd3-0fb1093e2ce0)
![Frequency Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/36902073-1f68-4fc4-b85a-dd15d9ae755f)
![Time Sink](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/04ea58e7-dfff-45c8-a248-4a9e3e0a96d7)


## Working GUI & AM Radio 
Overall this is the window that would pop up if the project were to be run. As you can see the "GUI Range" variables are displayed at the top with some sliders to allow changes to its values. As for the graphs below you can see the waterfall display showing the intensity of the current frequency range, and the frequency sink displaying the FFT of the incoming signals.    

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ac6e1b5d-71ec-4cf5-a4fa-30a28f6af287)

## Uses of FSK
Overall FSK



#### WORK IN PROGRESS 
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3514d22f-b6ae-43eb-9500-9d6d3f21f902)

Vector Source (-1,1) 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/05354ecd-4868-48e7-be3b-775ec43b124e)

Vector Source (-1,-1,-1,-1, 1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/989fd9b1-22d0-4b2e-9cbe-993da127094d)


Vector Source (1,1,1,1, -1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/39cf01f6-7c9e-4a5c-a73e-6656591dcfc2)

Vector Source (1,-1,1,-1, 1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ee5c38fd-1ade-44e6-8e32-de512dee45ba)


Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/1a633756-a66b-4275-9334-4c4b38f45a2f)

Big FSK Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ba88a43e-8f46-4a2e-aab1-cd4728574895)

Small FSK  Deviation Vector Source (-1,-1,-1, 1, 1, 1, -1,-1,1,1,-1,1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/634c0d5f-b5af-4604-8be0-11cf0292df00)
