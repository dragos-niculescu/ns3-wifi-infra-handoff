# ns3-wifi-infra-handoff

Based on ns-3.22 with the patch https://github.com/dlinknctu/OpenNet/blob/master/ns3-patch/sta-wifi-scan.patch
we implement wifi handoff over the infrastructure as follows
- server and APs are separated only by layer 2 switches, APs as bridges
- mobile scans channels 1-11 and chooses the AP with the best SNR
- mobile associates, and sends a broadcast packet over L2 so that all traffic is redirected from server 
- test script has a mobile cruising along 3 APs on channels 1, 6, 11

How to run: 
- tar xjvf ~/Downloads/ns-allinone-3.22.tar.bz2
- cd ns-allinone-3.22/ns-3.22
- patch -p1  < wifi-infra-handoff.patch
- cp wifi-infra-handoff.cc scratch 
- ./waf --run wifi-infra-handoff
- wifi-5-1.pcap shows traffic at the station 
