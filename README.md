# GE-808

### Overwiew
Guitar stompboxes prices for **one** start from around 100PLN, now why would we spend so much money if we could use our **STM F407VG**? 
The main goal concept of this project is to digitally modify a guitar signal and output it to audio jack.
### Description
The guitar signal is sent through [this circuit](https://prnt.sc/nxadeb) to ADC pin->PC3.  
Next step for our wave is ADC conversion, thanks to it we get signal in values from 0 to 4095 with our analog 0 roughly in the middle of digital range.
Modifying the points from ADC implementing various effects are possible. 
The last point is sending the modified data into I2S sound interface which was made easy thanks to [MYaqoobEmbedded](https://www.youtube.com/channel/UC-CuJ6qKst9-8Z-EXjoYK3Q).
In summary, the signal is carried in this fashion:
```
                     DMA_Transmission
                            ▼
Guitar--->Circuit--->ADC----*---->I2S--------->Audio jack
```
Where '*' is the point where ~~the magic happens~~ ADC interrupt allows to access the signal value and modify it.

The four buttons on our casing allow the player to hear his guitar with:
* Echo,
* Tremolo,
* Distortion, 
* or a Clean sound.
### Tools
The project was compiled with built-in __gcc__ compiler included in System Workbench for STM32, and written in __C/C++__ language.
__.ioc__ file was generated with STMCubeMX 5.0.1.
It bases on mechanisms listed below:
* I2S-CS43L22
* ADC Conversion
* DMA transmission
### How to run
Current version of the program is 1.0. 
Given you have the circuit and connected all the pins accordingly (based on __.ioc__ file) and built the project everything is straight-forward:
1. Connect usb port
2. Compile and send to STM32
3. Connect guitar jack into the socket
4. Connect your earphones/speaker.

LEDs above the buttons indicate the effect currently working. Simply press the button to change currently used signal modification.
```
| LED colour |   Effect       |
-----------------------------
|   WHITE    |   Clean        |
|   RED      |   Distortion   |
|   BLUE     |   Tremolo      |
|   GREEN    |   Echo         |
```
### How to compile
Simply import the project into [Eclipse System Workbench for STM32](http://www.openstm32.org/System%2BWorkbench%2Bfor%2BSTM32) and use **compile** button or **Ctrl+F11** 
### Future improvement
###### There is no bugs to be found, additional changes could be:
* Make effects connect with each other
* Replacing LEDs for a Nokia or E-paper screen
* Changing TL081 for more dedicated, sound-oriented op-amp 
* Potentiometer effect parameters adjusting
* Stacking **more** effects
### Attributions
Schematics for modyfing guitar signal based on [this thread](https://www.diystompboxes.com/smfforum/index.php?topic=102931.0).
Program uses I2S Audio Codec - CS43L22 functions acquired from [here](https://www.youtube.com/watch?v=QIPQOnVablY).
DMA connection based on [this video](https://www.youtube.com/watch?v=acJ_kSEU0V0).
### Licence
This project is created on MIT License.
### Credits
[Rafał Ewiak](https://github.com/Evenlaxxus) & [Wojciech Kulczak](https://github.com/wkulczi)

The project was conducted during the Microprocessor Lab course held by the Institute of Control and Information Engineering, Poznan University of Technology.
Supervisor: [Tomasz Mańkowski](https://github.com/Tomasz-Mankowski)
