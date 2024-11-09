# Puzzle 1:
The circuit is designed to work together with:

 - A nine-by-nine connectors grid
 - Three cables
 - Three RG LED as indicators

The goal of the circuit is detect which cable is connected to which connector. The position of the connection results in progression of the puzzle.
## The idea:
The cables are connected to three digital outputs. The digital outputs is enabled one by one. Each position of the nine by nine grid is connected to a digital input. if the digital input becomes high, the position is checked vs the currently active digital output.
In total, 81 digital inputs and 3 digital outputs are required, which is more than standard microcontrollers contain. 
### GPIO expander
To handle the high amount of digital inputs and outputs, a GPIO expander is selected. The flexibility of the design is important. Therefor a GPIO expander is selected that can handle both 5V and 3.3V. [PCA9555](https://mou.sr/3AClXk6) from NXP was selected as an GPIO expander. The chip handles 3.3V and 5V. The GPIO expander is controlled via I2C communication, with settable addresses via 3 pins. This means that a total of 9 chips can be combined in one I2C bus. The PCA9555 has 16 configurable GPIO's. The digital outputs can deliver 50 mA per output total, and the polarity can be inversed.

### Additional
To give visual feedback, three RG LED are added to the circuit. The design now is based on 5V source. The selected RG's selected are [WP819SURKMGKW](https://mou.sr/3Chk2C6) from Kingbright. The forward voltage is 1.8 and 2.1 V typical. 30mA is typical allowed current for this LED. Therefore, 120 ohm resistors are placed on each LED.
Since the board contains parts that might break over time, interfaces are added to the board instead of the components themselves. For the connectors, nine JST connectors with nine pins are selected. For the main connection, a four pin JST connector was selected. To keep the BOM small, the same connectors are selected for the LED connections and the cable connections.
Since everything will be hand soldered, all components are selected to be ok to hand solder, like 0603 for the resistors and SO24 for the chip.