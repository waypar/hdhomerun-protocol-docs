# HDHomeRun Protocol Documentation
Unofficial documentation of the HDHomerun protocol.


## Useful documents
libhdhomerun - https://github.com/Silicondust/libhdhomerun
hdhomerun_config docs - https://info.hdhomerun.com/info/hdhomerun_config
HDHomeRun HTTP Development Guide - https://www.silicondust.com/hdhomerun/hdhomerun_http_development.pdf
Tech/HDRack Operations Manual - https://www.silicondust.com/hdhomerun/hdhomerun_tech.pdf
HDHomeRun Development Guide (20110518) - https://www.silicondust.com/hdhomerun/hdhomerun_development.pdf
https://github.com/snemetz/synology/blob/master/HDHomeRun/Doc-APIs.md
https://github.com/jblachly/dvr/blob/master/HDHomeRun_notes.md

## Packet format
The packet format is explained here, it seems to be used for both UDP and TCP messages.
https://github.com/Silicondust/libhdhomerun/blob/b0e5d5f5c8e2bf37dea34beb014e08ebb598ebf6/hdhomerun_pkt.h#L25

## Discovery

A broadcast UDP discovery packet is sent by a client device on port 65001.

Once a valid discovery reply is received by the client a TCP connection is made on port 65001.

Channels app will send `{'3': '/tuner0/lockkey\x00', '4': '3733835452\x00'}` if you select "Scan for channels"

## HTTP endpoints

HDHomerun server provides the following endpoints, I believe on port 5004 and 80.

/discover.json
An example from npvrProxy.
```
{
“BaseURL”: “http://localhost:5004”,
“DeviceAuth”: “test1234”,
“DeviceID”: “12345678”,
“FirmwareName”: “hdhomerun4_dvbt”,
“FirmwareVersion”: “20150826”,
“FriendlyName”: “npvrProxy”,
“LineupURL”: “http://localhost:5004/lineup.json”,
“ModelNumber”: “HDHR4-2DT”,
“TunerCount”: 2
}
```
/discover.xml
/lineup.json
/lineup.xml

## Models/firmware
From https://www.silicondust.com/support/linux/

HDHR-US (hdhomerun_atsc)
HDHR-EU (hdhomerun_dvbt)
HDHR3-US (hdhomerun3_atsc)
HDHR3-DT (hdhomerun3_dvbt)
HDHR3-EU (hdhomerun3_dvbtc)
HDHR3-CC (hdhomerun3_cablecard)
HDHR3-4DC (hdhomerun3_dvbc)
HDHR4-2US (hdhomerun4_atsc)
HDHR4-2DT (hdhomerun4_dvbt)
HDHR4-2IS (hdhomerun4_isdbt)
HDTC-2US (hdhomeruntc_atsc)
HDHR5-2US/4US (hdhomerun5_atsc)
HDHR5-4DC (hdhomerun5_dvbc)
HDHR5-2DT/4DT (hdhomerun5_dvbt)
HDVR-2US/4US-1TB (hdhomerun_dvr_atsc)
HHDD-2TB (hdhomerun_hdd)

## Device ID
Device ID's seem to require fitting a particular checksum, see https://github.com/Silicondust/libhdhomerun/blob/b0e5d5f5c8e2bf37dea34beb014e08ebb598ebf6/hdhomerun_discover.c#L528


## Further links
https://forums.plex.tv/t/hdhomerun-emulator/156498/2
https://tvheadend.org/issues/4461

## Useful software
https://github.com/TheJF/antennas

https://github.com/xteve-project/xTeVe
