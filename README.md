# Li-Fi
Transferring data using Li-Fi (Light Fidelity)  
Li-Fi (light fidelity) is a bidirectional wireless system that transmits data via LED or infrared light. It was first unveiled in 2011 and, unlike Wi-Fi, which uses radiofrequency, Li-Fi technology only needs a light source with a chip to transmit data through light waves. This project transmits audio which is accepted from an auxiliary input and SD card. There are 2 approaches to this,  

### Method-1  
A transistor can be used as an LED driver and an audio amplifier simultaneously at the transmitter and an op-amp IC can be used at the receiver side.  

### Method-2  
One can either use an ADC (Analog to Digital Converter) at the transmitter and a DAC (Digital to Analog Converter) at the receiver to communicate.  

This project focuses on Method-1.  

## Transmitter  
The transmitter uses a transistor (BC548) as an audio amplifier as well as an LED driver. The input can either be from an aux cable or an SD card. To receive the input from the SD card, an Arduino is used with the SD card module to process the audio from the SD card. An audio file can’t be copied straight to the SD card, the file needs to be converted to .wav format and the bit rate should be specified in the code which is uploaded to the Arduino, also the audio should be changed from stereo to mono.  The code once executed displays all the files which are there in the root of the SD card, detects .wav files, and plays them. The volume can be controlled by changing the value in line 24 of the code (audio.setVolume(5);    //   0 to 7. Set volume level).  Analog pin A2 when grounded plays the next file and A3 when grounded pauses and plays the file (Both hold until they are disconnected from the ground). A switch is used to switch from auxiliary to SD card input. An LED connected to the collector of the transistor transmits the data to the receiver. ![Transmitter](Transmitter.jpg)
## Receiver  
The receiver uses an op-amp IC to amplify the signal which it receives from the solar panel. Instead of a solar panel, LDR (Light Dependent Resistor) can be used to receive the light input from the LED. The solar panel creates a small voltage that carries the data it received from the transmitter LED. The Op-amp amplifies this input and through a channel of capacitors, it is filtered and played using a ¼ watt speaker. To the gain of the IC pin, 1 and 8 are connected to a capacitor of 10µF which sets the gain to 10. The value of the capacitor sets the gain of the IC. A preset is used with the pins of the solar panel to control the output power or volume.
![Receiver](Receiver.jpg)
