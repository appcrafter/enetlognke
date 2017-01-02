# enetlognke

enetlognke is an OSX NKE (network kernel extension) that demonstrates the interface filter KPI (kernel programming interface). It has two different features:

* it will log packets being transferred via the interface

* it can, optionally, delay packets being transferred via the interface

See the Read Me.txt file for instructions.

This project has the code signing turned off. You can turn it on in the Build Settings if necessary.


The message part of the output to the system log is like this:




```enetlognke out IPv4 00146c8c909c|3d27c6e7f2fa|0800|45000034   66```

This is a list of space-separated items, as follows
 1. The text "enetlognke" is just here to ensure this text comes from our kext.
 2. The caller info. 'in' indicates the data was triggered by a system call to enetlognke_input_func, 'out' means a call was done to enetlognke_output_func 
 3. The protocol. We recognise IPv4, IPv6 and UNSPECified.
 4. Packet summary info as detailed below
 5. The packet byte count
 6. repetition mark: if this packet was seen before, '+' is added at the end of the line

The packet summary info contains a '|' separated list of the following values (see also https://en.wikipedia.org/wiki/Ethernet_frame)
 1. destination MAC address
 2. source MAC address
 3. protocol/length field. Typically 0x0800 indicating IPv4. 
 4. First data bytes
 
 
 This is a copy of Apple's enetlognke (https://developer.apple.com/library/content/samplecode/enetlognke/Introduction/Intro.html).  I made copy because (1) Apple does not provide all required files, eg xcode files are missing (2) the code does not work 100% on Sierra.

