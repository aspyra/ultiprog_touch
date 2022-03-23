# Trackstar Turbo Program Box analysis

description, photos TBD

---
## Commands list

|HEX|DEC|Takes argument|Response length|Function|
|:-:|:-:|:-:|:-:|-|
|D5|213|no|1 byte|Discover device?|
|D7|214|no|4 bytes|Read device ID|
|D8|215|no|20 bytes|Read settings|
|DE|222|no|1 byte|Reset settings to default values|
|DF|223|no|1 byte|Save changes to EEPROM?|
|E1|225|[yes](#operation-mode-(0xE1))|1 byte|Set Operating Mode|
|E2|226|[yes](#drag-brake-(0xE2))|1 byte|Set Drag Brake|
|E3|227|[yes](#voltage-cutoff-(0xE3))|1 byte|Set Voltage Cutoff|
|E4|228|[yes](#punch-profile-(0xE4))|1 byte|Set Punch Profile|
|E5|229|[yes](#brake-strength-(0xE5))|1 byte|Set Brake Strength|
|E7|231|[yes](#initial-brake-(0xE7))|1 byte|Set Initial Brake|
|E8|232|[yes](#neutral-deadband-(0xE8))|1 byte|Set Neutral Deadband|
|E9|233|[yes](#boost-timing-(0xE9))|1 byte|Set Boost Timing|

---
## Command arguments

An argument is sent ~22ms after the command as a single byte. The ESC immediatelly responds with 0x01. 

### Operation Mode (0xE1)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|Forward/Brake|
|__01__|__1__|__Forward/Reverse/Brake__|
|02|2|Forward/Reverse|

### Drag Brake (0xE2)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|0%|
|__01__|__1__|__5%__|
|02|2|10%|
|03|3|15%|
|04|4|20%|
|05|5|25%|
|06|6|30%|
|07|7|35%|
|08|8|40%|
|09|9|Custom value|

### Voltage Cutoff (0xE3)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|None|
|1E|30|3.0V/cell (6.0V)|
|__20__|__32__|__3.2V/cell (6.4V)__|
|22|34|3.4V/cell (6.8V)|
|23|35|3.5V/cell (7.0V)|

### Punch Profile (0xE4)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|Level 1|
|01|1|Level 2|
|02|2|Level 3|
|03|3|Level 4|
|04|4|Level 5|
|05|5|Level 6|
|__06__|__6__|__Level 7__|
|07|7|Level 8|
|08|8|Level 9|

### Brake Strength (0xE5)
|HEX|DEC|Value|
|:-:|:-:|-|
|32|50|50%|
|3C|60|60%|
|4B|75|75%|
|__50__|__80__|__80%__|
|55|85|85%|
|5A|90|90%|
|64|100|100%|

### Reverse Speed (0xE6)
|HEX|DEC|Value|
|:-:|:-:|-|
|19|25|25%|
|32|50|50%|
|__4B__|__75__|__75%__|
|64|100|100%|

### Initial Brake (0xE7)
|HEX|DEC|Value|
|:-:|:-:|-|
|__C8__|__200__|__same as drag brake__|
|0A|10|10%|
|14|20|20%|
|1E|30|30%|
|28|40|40%|

### Neutral Deadband (0xE8)
|HEX|DEC|Value|
|:-:|:-:|-|
|01|1|1%|
|__03__|__3__|__3%__|
|05|5|5%|
|08|8|8%|

### Boost Timing (0xE9)
|HEX|DEC|Value|
|:-:|:-:|-|
|__00__|__0__|__0 degrees (blinky)__|
|01|1|1 degrees|
|02|2|2 degrees|
|03|3|3 degrees|
|...|...|...|
|3C|60|60 degrees|

### Turbo Slope (0xEA)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|3 degrees / 0.1s|
|01|1|6 degrees / 0.1s|
|02|2|12 degrees / 0.1s|
|__03__|__3__|__18 degrees / 0.1s__|
|04|4|24 degrees / 0.1s|
|05|5|Fastest|

### Temperature Set (0xEB)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|Off|
|__01__|__1__|__On__|

### Boost Timing (0xEC)
|HEX|DEC|Value|
|:-:|:-:|-|
|__00__|__0__|__0 degrees (blinky)__|
|01|1|1 degrees|
|02|2|2 degrees|
|03|3|3 degrees|
|...|...|...|
|1E|30|30 degrees|

### Boost Timing RPM (0xED)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|2000 RPM|
|01|1|2500 RPM|
|02|2|3000 RPM|
|03|3|3500 RPM|
|__04__|__4__|__4000 RPM__|
|05|5|4500 RPM|
|06|6|5000 RPM|
|07|7|5500 RPM|
|08|8|6000 RPM|
|09|9|6500 RPM|
|0A|10|7000 RPM|
|0B|11|8000 RPM|
|0C|12|9000 RPM|
|0D|13|10000 RPM|
|0E|14|11000 RPM|
|0F|15|12000 RPM|
|10|16|13000 RPM|
|11|17|14000 RPM|
|12|18|15000 RPM|

### Turbo Delay (0xEE)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|No delay|
|01|1|0.05s|
|__02__|__2__|__0.1s__|
|03|3|0.15s|
|04|4|0.2s|
|05|5|0.25s|
|06|6|0.3s|
|07|7|0.35s|
|08|8|0.4s|

### Boost Timing ACC (0xEF)
|HEX|DEC|Value|
|:-:|:-:|-|
|00|0|50RPM/degree|
|__01__|__1__|__100RPM/degree__|
|02|2|150RPM/degree|
|...|...|...|
|0D|13|700RPM/degree|

### Drive Frequency (0xF0)
|HEX|DEC|Value|
|:-:|:-:|-|
|__00__|__0__|__8kHz__|
|01|1|16kHz|
|02|2|24kHz|

### Brake Frequency (0xF1)
|HEX|DEC|Value|
|:-:|:-:|-|
|__00__|__0__|__1kHz__|
|01|1|2kHz|
|02|2|4kHz|
|03|3|8kHz|
|04|4|16kHz|

