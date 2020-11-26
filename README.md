# hdhomerun-protocol-docs
Documentation of the HDHomerun protocol


## Useful documents
libhdhomerun - https://github.com/Silicondust/libhdhomerun
HDHomeRun HTTP Development Guide - https://www.silicondust.com/hdhomerun/hdhomerun_http_development.pdf
Tech/HDRack Operations Manual - https://www.silicondust.com/hdhomerun/hdhomerun_tech.pdf

## Discovery

A UDP discovery packet is sent by a client device on port 65001.
https://github.com/Silicondust/libhdhomerun/blob/b0e5d5f5c8e2bf37dea34beb014e08ebb598ebf6/hdhomerun_pkt.h#L25

Once a valid reply is received a TCP connection is made on port 65001.

Channels app will send `{'3': '/tuner0/lockkey\x00', '4': '3733835452\x00'}` if you select "Scan for channels"
