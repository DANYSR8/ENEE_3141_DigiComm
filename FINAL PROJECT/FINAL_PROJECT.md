# GPS Tracker with ASK Transmitter 

## Project Concept 

This project idea is a continueation of a pervious project where the idea was to implement a GPS location module that would get location inodfarion of the modulae itself, Which would then be proscces by a microprocessor. This process data is then sent to a GMS/SIM module where the idea was that this module would send the data to a phone. This ultimely did not work due to diffcuitly in setting up the SIM card.

This setback lead to this project where insted of using a GMS/SIM module it was switched out with an ASK 433mHz Transmitter and Reciver. This allowed for a quick and reailable way to transmitted the GPS data and have a plan expand this project.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/dd50e90b-ae71-4a4b-823d-92cc147fd82a)


## SETUP & Checking Modules Works
### Checking ASK Modules 

To check that this ASK Transciver was working a quick tutorial was followed, and the module were wired as dislayed in the two figures below.   

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6aec165d-5470-423c-85c1-3214c24a996a)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/c53f64e1-1265-4a8b-8e16-dd2334afa2b4)

Having the modules set up with the two arduinos as displayed above, a simple ON and OFF signal was used to simualate a digital signal and see if the the transmitter is working. To dectect and see the transmitter working SDR Console was used to easilty detect the signals around the 433.92MHz carreir. Three dirffent digital signal sequence where ues to ensure that we were seeing the actual transmited signal and just not noise. The figure below displays each digital sequence used and there repective spectrum. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b3d45b76-8264-4af3-aff4-816883333f67)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4fa869d9-c458-464d-b7d1-ca33a7329932)


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7eddf140-73b3-4697-8139-1bc3e1483124)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4f1d8b49-f087-4ab0-8a7a-f7935f8eee2b)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b78a3f6f-c7ef-4d35-a79d-dee7c8383080)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bddb2e2c-e938-4617-9d01-47f71666ed3f)





### Fixing ASK Transmitter

When anaylsing the spectrum previous the magtuie for the spike were very weak. So a step back was taken and it was recongise that the trasnmirtter was missing a coil that would help with transmittion of the signal. This coil is outline in the figure belew, once this comeponet was added back into the module a much clearler and signal can be observed. Additionally we change the data being transmitted to be a "char" array which was ultimely trasnitted as ASCII values.   

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/1c37e4c0-9a4f-44cf-b86c-6f8bdd9e8ff1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7a635884-cb5b-4c52-bfac-75fc8c9fc4e7)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9e8c4fc4-f4b0-43be-ac65-d8767a85d575)

Additionlly too see the modulated data GNU Radio was used to form the flow diargram seen below as well as display the frequency and time domain the the modulated signal.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b6773eeb-9f63-4ed2-9b02-7f462aeaa49c)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9f572eed-3886-4e58-818c-903ee3ac6908)


###  Converting ASCII to Readable Text 

Now on the reciver side of the project the data the code displayed below can be use to convert the ASCII to readable text. In this case the message was hard coded to send one specigly message being hello. 

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/168849a4-8ce3-430a-af99-07e104afe273)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/63366e98-8243-419b-9597-fd731c329103)

### Setting Up GPS 

Back to the transmitter side the next step involved setting up the GPS module. Which is stright foward by coneting the corresponding TX and RX pins to the ardunio and  using the liabry and corresponiding function displayed below. The module can be finicking if used inside, it recomded that it would be close to window inorder to have a stable connection to recieve data.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3801ade6-6dee-4c21-af2e-7ba83c1ad4b7)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d4eaa2a6-7b41-4979-a3bc-3481440230df)

Having this data being gather by the GPS module all that is left is to send the data through the transmitter module.


### Decoding the Trasnmitted GPS Data 
GPS SENDINF THROUGH THE TRANMITTE NEED TO CONVERT TO ASCIIT FROM HEX 

Now having the GPS data being sent we can set up the recivcer end of the system with the code seen below. This will convert he data transmited data being sent as doubles to a string which is then display in the serial monitor.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ca3ec31f-d588-4e44-9eec-ec4bc2726347)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/32af07e1-0d7e-4734-aad3-6379d6f6feb6)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ee4e83ea-6945-49b0-9dac-de14ff3eb5c0)


As we can see above the coresponding data if it were to be comapred and  tranlated using the ASCII Table we see that the data correspons to 39.68 which is the correct values for the latidtuide. 
