# The Basics

## Downlink Format
*The 1090MHz Riddle* [Message Structure](https://mode-s.org/decode/adsb/introduction.html#message-structure)\
*pyModeS* [`pyModeS.df(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

The *downlink format* indicates message the message type.

DF | Type
---|-----
0 | Short air-air surveillance (ACAS)
1 - 3 | Reserved
4 | Surveillance, altitude reply
5 | Surveillance, identify reply
6 - 10 | Reserved
11 | All-call reply
12-15 | Reserved
16 | Long air-air surveillance (ACAS) 
17 | Extended squitter
18 | Extended squitter / non transponder
19 | Military extended squitter
20 | Comm-B, altitude reply
21 | Comm-B, identify reply
22 | Reserved for military use
23 | Reserved
24 | Reserved Comm-D (ELM)

## ICAO
*The 1090MHz Riddle* [ICAO Address](https://mode-s.org/decode/adsb/introduction.html#icao-address)\
*pyModeS* [`pyModeS.icao(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

All aircraft are assigned a unique twenty-four bit address. All messages originating from an aircraft will this to associate message data with the aircraft. The function [`pyModeS.is_icao_assigned(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py) verifies that the ICAO code embeded in a message falls within a range of assigned codes.

## Cyclic Redundancy Check
*The 1090MHz Riddle* [ADS-B Checksum](https://mode-s.org/decode/adsb/introduction.html#ads-b-checksum)\
*pyModeS* [`pyModeS.crc(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

Mode-S messages use Cyclic Redundancy Check (CRC) to verify data integrity. If the data is valid, the CRC remainder will be 0.