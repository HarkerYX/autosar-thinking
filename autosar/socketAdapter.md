In the legacy Ethernet communication Socket is the end point of the communication. and the each application will be bind with the socket connection to send or receive the data over the Ethernet. however in the autosar communication it is totally different. the end point of the vehicle communication is the PDU (packet data unit) or the signal (which are bind with the PDU) and Autosar application only concerns about the Signal and Autosar COM module deal with PDU irrespective of the used communication protocol in the physical layer.

Therefor to complaint with legacy practice of AUTOSAR communication stack , SoAD (Socket Adapter) module has been introduced in Ethernet AUTOSAR stack to bind socket connection with the PDU. so that COM and application layer will behave in the same irrespective of the down layer protocol i.e CAN, Flexray or Ethernet.





# Reference

1. https://autosaracademy.com/socket-adaptor-soad/