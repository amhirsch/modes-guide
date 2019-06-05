# Mode-S Guide
This guide presents an overview of Mode-S message decoding.
It is organized as a flowchart to understand what information can be extracted from each message.
For a technical understanding of Mode-S messages, visit [The 1090MHz Riddle](https://mode-s.org/decode/).

## The Basics

### Downlink Format
*The 1090MHz Riddle* [Message Structure](https://mode-s.org/decode/adsb/introduction.html#message-structure)\
*pyModeS* [`pyModeS.df(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

The *downlink format* of a message indicates Mode-S message type.\
Here are select few message types:

DF | Type
---|-----
17 | ADS-B Out
18 | TIS-B
20, 21 | Comm-B

### ICAO
*The 1090MHz Riddle* [ICAO Address](https://mode-s.org/decode/adsb/introduction.html#icao-address)\
*pyModeS* [`pyModeS.icao(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

All aircraft are assigned a unique transponder identifier. All ADS-B messages will include this to associate message data with an aircraft. The function [`pyModeS.is_icao_assigned(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py) verifies that the ICAO code embeded in a message falls within a range of assigned codes.

### Cyclic Redundancy Check
*The 1090MHz Riddle* [ADS-B Checksum](https://mode-s.org/decode/adsb/introduction.html#ads-b-checksum)\
*pyModeS* [`pyModeS.crc(msg)`](https://github.com/junzis/pyModeS/blob/master/pyModeS/decoder/common.py)

Mode-S messages use Cyclic Redundancy Check (CRC) to verify data integrity. If the data is valid, the CRC remainder will be 0.