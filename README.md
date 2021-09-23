# saab-93NG-IBUS
A collection of known I-BUS messages found in 2002/2003+ second-generation SAAB 9-3's. PR's welcome.

Single-Wire GM-LAN Bus, 33.33kbps

Messages are presented byte-wise, where **b0** is the least-significant-byte.
States are represented in binary and hex, and are provided with a human-readable description.

## BY ID
### 0x91
    - b1
        - 00000000 (00) Cruise control on
        - 00100000 (20) Cruise control off
### 0x108
    - These are wrong atm.
    - b0:b1
        - 16 bit integer for turbo boost (percentage I believe)
    - b2:b3
        - 16 bit integer for RPM
    - b4:b5
        - 16 bit integer for KPH
### 0x220
    - b1:b2
        - Steering wheel angle (16 bit special integer)
        - When MSB is 0, decode as regular 16 bit integer (b1 << 8) + b2.
        - When MSB is 1, subtract 65536 from (b1 << 8), before adding with b2.
        - This results in a range of ~-8600 to ~+8600 representing full wheel range (lock to lock).
        - Unsure what the real-world angle-equivalent of this value is (yet).
### 0x290
    - b0
        - 00000001 (01) Windshield washer (pull stick fully in)
        - 00000100 (04) Horn
        - 00010000 (10) Flash high beams (pull stick halfway)
        - 00011000 (18) Toggle high beams (pull stick fully in)
    - b1
        - 00000001 (01) Wiper single
        - 00001010 (0A) Wiper intermittent
        - 00001011 (0B) Wiper slow
        - 00001101 (0D) Wiper fast
    - b3
        - 00000000 (00) Default
        - 00000001 (01) Volume UP
        - 00000010 (02) Volume DOWN
        - 00000011 (03) SRC button
        - 00000100 (04) Voice activation button
        - 00000101 (05) Seek forward
        - 00000110 (06) Seek backward
        - 00010001 (11) NXT button
        - 00010010 (12) Phone button
    - b4
        - 00000000 (00) Default
        - 00000100 (40) Indicator right
        - 00001000 (80) Indicator left
### 0x300
    - b1
        - Light control panel mode
        - 00000000 (00) OFF
        - 00101000 (28) Daytime lights
        - 00011000 (18) Low-beam lights
### 0x310
    - b1
        - SID-C ESP button
        - 00000000 (00) OFF
        - 00000001 (01) Pressed
    - b5
        - SID-C Spare button
        - 00000000 (00) OFF
        - 00100000 (20) ON (Toggle)
### 0x320
    - b0
        - Locking status / controls 
        - 00010000 (10) Driver unlocked
        - 00010001 (11) Driver locked
        - 00010100 (14) Unlock Button
        - 00011001 (19) Lock Button
    - b1
        - Mirror adjustment, triggered by d-pad
        - 00000000 (00) Default
        - 10000000 (80) Adjustment in progress
    - b3
        - Mirror adjust DPAD direction (for left mirror only?)
        - 00010000 (10) LEFT
        - 00100000 (20) RIGHT
        - 01000000 (40) DOWN
        - 10000000 (80) UP
    - 
### 0x340
    - b0
        - Child lock active
### 0x350
    - b0
        - Child lock active
### 0x370
    - b0
        - Front fog lights / reversing light
        - 00000000 (00) OFF
        - 00000001 (01) REVERSE
        - 01000000 (40) ON
        - 01000001 (41) ON and REVERSE
### 0x380
    - b0
        - Brakes pressesd
        - 00000000 (00) Default
        - 00100000 (20) Brakes pressed
    - b1
        - Rear fog lights
        - 00000000 (00) OFF
        - 00100000 (20) ON
### 0x460
    - b0
        - 00000000 (00) Night mode off
        - 01000000 (40) Night mode on
    - b1:b2
        - Instrument lighting brightness levels 
        - Night mode brightness
        - Two independant 8 bit integers
    - b3:b4
        - Brightness sensor
        - 16 bit integer
### 0x520
    - b0
        - Years after 2000
        - 8 bit int
    - b1
        - Month
        - 8 bit int
    - b2
        - Day
        - 8 bit int
    - b3
        - Hour
        - 8 bit int
    - b4
        - Minute
        - 8 bit int
    - b5
        - Second
        - 8 bit int
