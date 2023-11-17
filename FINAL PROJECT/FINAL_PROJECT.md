# GPS Tracker with ASK Transmitter 

## Project Concept 

This project idea is a continuation of a previous project where the objective was to implement a GPS location module to acquire location information of the module itself. This information would then be processed by a microprocessor. The processed data was intended to be sent to a GSM/SIM module with the idea of transmitting this data to a phone. However, this plan ultimately didn't work due to difficulties encountered in setting up the SIM card.

As a result of this setback, a new approach was adopted for this project. Instead of utilizing a GSM/SIM module, it was replaced with an ASK 433MHz Transmitter and Receiver. This modification allowed for a quick and reliable transmission of the GPS data and laid the groundwork for expanding this project.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/dd50e90b-ae71-4a4b-823d-92cc147fd82a)


## SETUP & Checking Modules Works
### Checking ASK Modules 

To verify the functionality of the ASK Transceiver, a brief tutorial was followed, and the modules were connected as illustrated in the two figures below.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/6aec165d-5470-423c-85c1-3214c24a996a)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/c53f64e1-1265-4a8b-8e16-dd2334afa2b4)

Upon setting up the modules with the two Arduinos as illustrated above, a straightforward ON and OFF signal was used to emulate a digital signal, testing the functionality of the transmitter. To ascertain the transmitter's operation,  SDR Console  was uesd to effortlessly detecting signals within the 433.92MHz carrier range. Three distinct digital signal sequences were utilized to confirm the presence of the transmitted signal amidst potential noise. The figure below showcases each digital sequence utilized and their respective spectra, offering a comprehensive view of the transmitted signals' characteristics.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b3d45b76-8264-4af3-aff4-816883333f67)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4fa869d9-c458-464d-b7d1-ca33a7329932)


![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7eddf140-73b3-4697-8139-1bc3e1483124)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/4f1d8b49-f087-4ab0-8a7a-f7935f8eee2b)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b78a3f6f-c7ef-4d35-a79d-dee7c8383080)

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/bddb2e2c-e938-4617-9d01-47f71666ed3f)





### Fixing ASK Transmitter

When analyzing the previous spectrum, it can be seen that the magnitudes of the spikes were notably weak. After reassessing the setup, it was identified that the transmitter lacked a crucial coil that significantly aids in signal transmission. This missing component is outlined in the figure below. Once this component was reintegrated into the module, a significantly clearer signal became observable. Additionally, we opted to modify the transmitted data to a "char" array, ultimately transmitting it as ASCII values.   

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/1c37e4c0-9a4f-44cf-b86c-6f8bdd9e8ff1)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/7a635884-cb5b-4c52-bfac-75fc8c9fc4e7)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9e8c4fc4-f4b0-43be-ac65-d8767a85d575)

Additionlly too see the modulated data GNU Radio was used to form the flow diargram seen below as well as display the frequency and time domain the the modulated signal.  

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/b6773eeb-9f63-4ed2-9b02-7f462aeaa49c)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/9f572eed-3886-4e58-818c-903ee3ac6908)


###  Converting ASCII to Readable Text 

On the receiver side of the project, the code displayed below can be utilized to convert ASCII data into readable text. In this instance, the transmitted message was hardcoded to convey a specific phrase, which in this case was 'hello.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/168849a4-8ce3-430a-af99-07e104afe273)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/63366e98-8243-419b-9597-fd731c329103)

### Setting Up GPS 

Back to the transmitter side the next step involved setting up the GPS module. This process is straightforward, involving the connection of the respective TX and RX pins to the Arduino and utilizing the library with its corresponding functions, as demonstrated below. It's noteworthy that the module might exhibit sensitivity when used indoors; hence, it is advisable to position it near a window to ensure a stable connection for receiving data.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/3801ade6-6dee-4c21-af2e-7ba83c1ad4b7)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/d4eaa2a6-7b41-4979-a3bc-3481440230df)

Having this data being gather by the GPS module all that is left is to send the data through the transmitter module.


### Decoding the Trasnmitted GPS Data 

With the GPS data successfully transmitted, the receiver end of the system can now be configured using the following code. This code snippet is responsible for converting the received data, transmitted as doubles, into a string format. Subsequently, this converted data is displayed on the serial monitor for observation.

![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ca3ec31f-d588-4e44-9eec-ec4bc2726347)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/32af07e1-0d7e-4734-aad3-6379d6f6feb6)
![image](https://github.com/DANYSR8/ENEE_3141_DigiComm/assets/117769464/ee4e83ea-6945-49b0-9dac-de14ff3eb5c0)


Certainly! Here's a refined version:

As observed above, upon comparing and translating the corresponding data using the ASCII Table, we find that the data corresponds to '39.68,' which represents the accurate values for the latitude.
