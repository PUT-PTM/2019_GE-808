# GE-808

### Overwiew
Guitar stompboxes prices for **one** start from around 100PLN, now why would we spend so much money if we could use our **STM F407VG**? 
The main goal concept of this project is to digitally modify a guitar signal and output it to audio jack.
### Description
The guitar signal is sent through [this circuit](https://prnt.sc/nxadeb) to ADC pin->PC3.
Next step for our wave is ADC conversion, thanks to it we get signal in values from 0 to 4095 with our analog 0 roughly in the middle of digital range.
The signal is carried in this fashion
```
                     DMA_Transmission
                            ▼
Guitar--->Circuit--->ADC----*---->I2S--------->Audio jack
```
Where '*' is the point where ~~the magic happens~~ ADC interrupt allows to access the signal value and modify it.
### How to run
### How to compile
Simply import the project into [Eclipse System Workbench for STM32](http://www.openstm32.org/System%2BWorkbench%2Bfor%2BSTM32) and use **compile** button or **Ctrl+F11** 
### Future improvement
###### There is no bugs to be found, additional changes could be:
* Make effects connect with each other
* Replacing LEDs for a Nokia or E-paper screen
* Changing TL081 for more dedicated, sound-oriented op-amp 
* Potentiometer effect parameters adjusting
* Stacking more effects
### Attributions
Schematics for modyfing guitar signal based on [this thread](https://www.diystompboxes.com/smfforum/index.php?topic=102931.0).
Program uses I2S Audio Codec - CS43L22 functions acquired from [here](https://www.youtube.com/watch?v=QIPQOnVablY).
### Licence
This project is created on MIT License.
### Credits
The project was conducted during the Microprocessor Lab course held by the Institute of Control and Information Engineering, Poznan University of Technology.
Supervisor: [Tomasz Mańkowski](https://github.com/Tomasz-Mankowski)
