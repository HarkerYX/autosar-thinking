In the legacy Ethernet communication Socket is the end point of the communication. and the each application will be bind with the socket connection to send or receive the data over the Ethernet. however in the autosar communication it is totally different. the end point of the vehicle communication is the PDU (packet data unit) or the signal (which are bind with the PDU) and Autosar application only concerns about the Signal and Autosar COM module deal with PDU irrespective of the used communication protocol in the physical layer.

Therefor to complaint with legacy practice of AUTOSAR communication stack , SoAD (Socket Adapter) module has been introduced in Ethernet AUTOSAR stack to bind socket connection with the PDU. so that COM and application layer will behave in the same irrespective of the down layer protocol i.e CAN, Flexray or Ethernet.

## Interaction of SoAD

![https://autosaracademy.com/wp-content/uploads/2021/09/Socket-Adaper-interaction-1.png](https://autosaracademy.com/wp-content/uploads/2021/09/Socket-Adaper-interaction-1.png)

As depicted in above interaction diagram, SoAD module interact with multiple module on upper side to send and receive data and down side interacting only with TCP/IP module.

- PduR responsible for sending and receiving application data
- DoIP will be handling Diagnostic related data
- SD (service discovery) will be taking care service discovery related data. i.e list of available services , subscribed services , etc
- TCP/IP offers the functionality to send and receive that internet protocol data.

## Functionality of SoAD module

SoAD provide the PDU based communication over TCP/IP network. Therefor I-PDUs are mapped with socket connection and configured in SoAD.

It is also possible to mapped multiple I-PDU with one socket connection by adding optional SoAD PDU header in-front of each I-PDU. this is to reduces the TCP/IP header over head for small I-PDU. where multiple I-PDU will be combined and sent on one TCP/IP massage.

Socket connection can be opened automatically automatically or manually via request from upper layer. For disconnection of socket procedure is defined.

SoAD does not provide any bit-byte Endianness handling for PDU.

### Socket connection:

An internet socket is endpoint of the communication link , which is defined by tuple of IP address and port. To abstract the communication SoAD define the socket connection and it specify the connection between local socket and remote socket and many other parameter i.e buffer requirement, transport protocol , and many more…

Each socket connection contain unique identifier.

**SoAd_MainFunction()** of SoAD is responsible to open socket connection which satisfy the defined criteria and close the connection which satisfy the closing criteria.

Each time when socket connection state changes SoAD will notify the upper layer using the notification function.



### PDU transmission:

For the transmission of the upper layer PDU , SoAD contains configuration which specify the PDU route linked to the socket connection. PDU route describe the path from upper layer module of SoAD till socket of TCP/IP stack (which specify other details of socket connection).

Upper layer module can use different method to transmit the PDU as described below:

- PDU transmit via IF-API
- PDU Transmission via IF-API and nPduUdpTxBuffer
- PDU Transmission via IfRoutingGroupTransmit API
- PDU Transmission via TP-API

each of these method contain different kind of handling while transmitting the PDU.



### PDU Reception:

For the reception of the PDU form TCP or UDP, SoAD configuration specify the route which refer to socket connection. socket route specify the route from TCP or UDP of the TCPIP stack to the upper layer module of the SoAD.

For receiving of PDU upper layer can use h different method avail by SoAD.

- PDU Reception via IF-API
- PDU Reception via TP-API (PDU Header disabled)
- PDU Reception via TP-API (PDU Header enabled)

each of these method contain different kind of handling while receiving the PDU.



### Buffer handling:

SoAD provide sufficient buffers to store the data which can’t be forwarded to upper layer within context of SoAD_RxIndication function call.

SoAD provide the sufficient buffer to store the data which can’t be forwarded to TCPIP.



# Reference

1. https://autosaracademy.com/socket-adaptor-soad/