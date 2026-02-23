
# IoT/ICS Communication Protocols

> This is just my notes on IoT/ICS communication.

## Table of Contents

- [IoT Protocol Stack](#protocol-stack)
- [Communication Ranges](#communication-ranges)
- [Controller Protocols](#controller-protocols)
- [Machine to Machine](#machine-to-machine)
- [Wired Connections](#wired-connections)
- [PAN RF](#pan-rf)
- [WAN RF](#wan-rf)
- [Routing Protocols](#routing-protocols)
- [Middleware](#middleware)
- [Field Energy Transfer](#field-energy-transfer)
- [Resources](#resources)

## Protocol Stack

Typically, IoT protocols can be an TCP/IP stack extension, but the common layers of the OSI model that IoT protocols work over are as follows:

- **Application Layer** - IoT applications, device management, etc.
- **Transport Layer** - Typically UDP and DTLS
- **Network Layer** - IP routing and IPv6 packets
- **Link Layer** - Traffic and device access

To further dive into this, there's a IoT version of the OSI model stack accoring to RF Wireless World. It's a bit of a stretch, but still a cool model to talk about, and I'm naming it the IoTSI (Internet of Things System Interconnection) model for the purposes of these notes.

1. **Physical Layer** - The communication between the real world and sensors. This uses magic sensor technology.
2. **Processing Layer** - How data gets processed. Microcontrollers and what not.
3. **Hardware Interface Layer** - How hardware talks to each other. CAN, SCI, SPI, I2C, and all that fun stuff. It's the 1s and 0s put onto voltage lines.
4. **RF Layer** - This is where we drop the wires and go into zapping electromagnetic signals across different ranges. This uses Wi-Fi, Bluetooth, Zigbee, Z-Wave, NFC, RFID, GSM, 5G, etc.
5. **Session Layer** - The OSI's application protcols such as MQTT, CoAP, HTTP, SSH, and FTP. It's how messages go to the cloud.
6. **User Experience Layer** - This is where the UI lies and data analytics and interfacing.
7. **Application Layer** - This one is just what the other layers do together and defines the functional system, I guess...

The IoTSI model is more focused on the functionality of the data over how the data transfer actually works, and misses a lot while trying to explain IoT networks since it assumes OSI integration.

## Communication Ranges

Devices can be networked either directly between endpoints, often in a master-slave configuration, or services can be hosted on the cloud, and each endpoint accesses the cloud, which brokers the service. Networks operate within different scales, so how far these devices can physically communicate with something is known as the computer networking scale. Let's break down near field communication, personal area networks, local area networks, wide area networks, and internet area networks.

### Near Field Communication (NFC)

NFC is a set of communication protocols that allow for wireless communication in distances of at most 4 cm. NFC is standardized by the IEC to utilizes frequencies of 13.56 MHz.

### Personal Area Networks (PAN)

PANs are when you connect to things nearby. PANs can go to the internet, but a lot of times its just inter-device connections in a single workspace. Bluetooth and Zigbee are the biggest examples of this.

### Local Area Networks (LAN)

When you think of networks, you think of LANs. Thanks to the mesh-like configuration of this network, devices can connect to the network within moderately large ranges without directly accessing the internet. This is the classic network definition, where devices all talk to each other in the LAN and then it collates into the gateway router that goes to the internet. Wi-Fi is the most popular one, but Ethernet is another common one. Arguably, Z-Wave devices can be considered a LAN.

### Wide Area Networks (WAN)

Wide area networks cover large ranges and are built either by Internet Service Providers or for individual organizations. WANs typically connect a bunch of lans using broadbands and leased lines, which are the circuits that cover long distances to transport information. WAN connections include cellular, satellite, radio, and fiber-optics. 

### Internet Area Networks (IAN)

Internet Area Networks are rising in popularity due to the increase of the virtualization of internet services. This means that services such as emails don't solely rely on endpoints, but instead occur via endpoints connecting to sessions controlled by the cloud. Large scale data centers manage the services, while endpoints simply connect to cloud using a broadband connection. IAN is a type of WAN, just talks about the cloud integration.

## Controller Protocols

### S7 (Siemens)

Siemens is at it again with their own special protocol for SIMATIC S7 PLCs. It runs on TCP/IP on port 102, originally for STEP 7, but typically can integrate with SCADA/MES systems. Snap7 is an open-source library that implements S7, and Wireshark even has dedicated packets for S7. Packets are ACK/NACKed, data can be read or written, and JOB requests are also sent to tell the S7 devices what to do. ROSCTR stores any errors.

### OpenPLC

OpenPLC integrates many languages into one space to enable controllers to be programmed for processes. OpenPLC has built in servers for things like Modbus and DNP3. It uses Ladder Diagrams and Functional Block Diagrams to let engineers prototype automation systems.

### Node-RED

Made by IBM, Node-RED is Scratch coding for System Engineers. It just uses block coding for automation application on controllers that support it. On the networking layers, the controllers will use protocols like Modbus or MQTT.

## Machine to Machine

### MQTT (Message Queuing Telemetry Transport)



### SNMP

SNMP runs on top of UDP, port 161 for queries and 162 for traps. There are managers and agents (master/slave configuration). Data is organized in the managment information base, and there are polling/active queries and traps, which are asynchronous notificaitons. SNMP is used in industrial equipment and networking equipment. SNMP also has different security features in each version. Version 1 & 2C uses plaintext strings, while Version 3 uses authentication and different layers of encryption. 

### IEC 60870-5-104

IEC 60870-5-104 is a protocol commonly used in telecontrol and SCADA. It allows for real-time telementry and control between control centers and field devices, where control centers are clients and RTUs/IEDs are servers. IEC 104 occurs over port 2404. In this protocol, each device gets a unique common address and data from field devices is held at information object addresses. 

### DNP3

DNP3 defines a set of communication protocols used in process automation systems, and typically integrates with operational technology such as remote terminal units (RTUs) and programmable logic controllers (PLCs). The goal of DNP3 is to collate all communication into the central human-machine interface/supervisory control and data acquisition (HMI/SCADA) node. 

### CoAP

Constrained Application Protocol (CoAP) uses UDP on IP for constrained devices. These devices that work best with CoAP are low-power or in lossy networks. It is made to be easily translated into HTTP as it is based off of the REST model. CoAP is available on most devices that support UDP, and has the ability to integrate DTLS.

### LwM2M (Lightweight Machine-to-Machine)

Open Mobile Alliance developed LwM2M for IoT device management. It is built on CoAP typically, but can support other transfer prtocols. It manages security credentials, firmware updates, and connectivity management. It can integrate DTLS or TLS, depending on what transfer protocol is integrated with LwM2M.

### Open Platform Communications (OPC)



### Profinet



### Modbus



### Omron FINS Host Link

Omron FINS Host Link uses the binary FINS protocol over TCP/IP and the Host Link protcol that uses ASCII-serial. Host link is master slave based, like any normal serial protcol, and is used to send commands to a PLC from an RTU. But FINS is unique, as it's Factory Interface Network Service, provided by OMRON. This allows PLCs to exchange data over TCP port 9600. It's functionally similar to modbus, where registers have bits for reading/writing, couting values, and sending data.

### BACnet

BACnet is a protocol for Building Automation and Control (BAC) networks and is typically used for fire detection, lighting, and HVAC systems. It is object oriented, defining analog and digital data types, and even has a logging object, and commands are focused on interfacing between sensors/actuators and controllers.

## Wired Connections

### Fieldbuses

Fieldbus is a standardized (IEC 61158) distributed communication network that is designed for real time systems, often utilizing ethernet. Fieldbus relies on connecting multiple devices in often a daisy-chain configuration which collates all devices on a primary bus to the master. IEC 61158 is the standardization of Fieldbus. It outlines required commands and reporting, along with the control scheme. This standardization accounts for a majority of modern Fieldbus protocols. Popular fieldbus protocols are used in Modbus, Profibus, CANbus, and BACnet. 

### CANBus

Controller Area Network (CAN) Bus is used for communication between electronic control units in vehicles. It is a brodcasting message protocol that is intended to reduce electrical wiring complexity as communication is multiplexed and relies on differential signals. 

### EtherCAT

EtherCAT (Ethernet for Control Automation Technology) leverages an IEC 61158 Fieldbus system over Ethernet in order to enable real-time computing in industrial applications. Synchronization is expected to be precise and low jitter with less than 1us of clock speed. In this system, an EtherCAT master has a large amount of slaves daisy chained together, and the master communicates with these slaves in a loop style. Typically, the master will have multiple ports connected to the slaves, enabling network redundancy, and have loopback switches that close on failure of the primary communication line, which connects a redundant communication line.

### HART (Highway Addressable Remote Transducer)

This one's neat. HART is a hardware point-to-point communication that uses analog and digital signals to communicate (at the same time!), leveraging 4-20 mA current loops on analog instruments and analog only host systems. HART defines the application of Bell 202, and is in multi-drop or point to point connections. Point to point is when the 4-20 mA loop current and digital signals are overlaid, and the controller is capable of processing both signaling protocols. Multi-drop fixes the loop current to 4 mA, and more instruments are able to be connected and communicate digitally with unique addresses.

## PAN RF

### Bluetooth & BLE

Bluetooth transmits data over short ranges in personal area networks. It uses the UHF band of 2.402 GHz to 2.48 GHz. This is IoT, though, so of course there is the embedded edition, Bluetooth Low Energy (BLE). BLE sends smaller data packets, is spread across different frequencies, and has sleep modes. It is incompatible with bluetooth, so most BLE chips have Bluetooth.

### Z-Wave

Z-Wave is a wireless ad hock network that operates in the sub-GHz band, around 900 MHz. It is low power and low-data rate. It is capable of mesh networking, where Z-Wave devices can repeat signals up to four hops to extend the network range, with up to 232 devices, and each device has a range of 70-100 meters. Z-Wave transmits with AES-128 encryption, and is typically used in smart homes. There is also a version of Z-Wave with an extended range that can reach miles.

### ZigBee

Zigbee is a low power communication wireless ad hock network. Zigbee defines the device management and application protocol, while IEEE 802.15.4 is the physical and link layer. It is a wireless mesh network that uses AES-128 encryption. IEEE 802.15.4 operates primarily in the 2.4 GHz band. It's used in smart homes usually, it is pretty much the same as Z-Wave but not proprietary.

## WAN RF

### 6LoWPAN

6LoWPAN is a low power WAN that uses IPv6. IPv4 and IPv6 can wrap any physical and link layers, but this defines the application between IP and the low-power devices. It also uses IEEE 802.15.4, like Zigbee.

### LoRaWAN

Long Range  is a radio communication on spread spectrum modulation. LoRa is the radio signal technology while LoRaWAN is the actual applicaiton. It is used for low-power devices over long distances. It uses sub gigahertz radio frequencies that are not liscenced, such as the bands 863 MHz to 928 MHz. It is especially used for transmitting positional information and it has datarates of 300 bits/s to 27 kbits/s.

### SigFox

Sigfox is a 0G low-power WAN that is in short range bands of 868 MHz and 902 MHz. Sigfox is designed to connect low power objects securely when they emit small amounts of data. It's proprietary, but functions like other LoWANs, where base stations connect IoT devices.

## Routing Protocols

Routers route, but IoT routers are special because they route in low power and harsh conditions. Let's talk about that magic.

### RPL (Routing Protocol for Low-Power and Lossy Networks)

RPL supports a wide range of link-layer protocols. RPL works by building a acryplic graph to find a single route for all traffic, which is stored at the root, while each node only knows it and its parents. When a node wants to communicate, it sends a request to communicate to its parent, which then propagates to the root, who decides how to trasmit data. RPL allows for storage and data management, and uses server technologies.

Since the root controls everything, this preserves any failure in nodes and reduces the amount of power demanded by eacy node.

## Middleware

Middleware for IoT networks integrates operating systems and embedded devices. It's primary goal is to take networked embedded devices and provide ambient intelligent application access on machines. Middleware services such as HYDRA enable secure applications for embedded devices, where peer to peer networking can be enabled, and identity management can be handled. Middleware allows for software applications to be significantly easier to develop with middleware that can natively handle embedded devices. Middleware projects and brands includes WhereX, HYDRA, InterDataNet, Z-Wave, and Convergence. Middleware is capable of managing security layers, device management, device locking, and policy enforcement.

To go back to the IoTSI model, layer 6 and 7 are possible without middleware, but it's very annoying. Middleware lets random CS kids able to make applications for IoT devices with without them needing to open the datasheets of any of the devices their app uses. It standardizes access between everything.

## Field Energy Transfer

Electromagnetic wave-icles move, which means they have energy. We generate a ton of these regularly, such as ARP broadcasts over Wi-Fi, or even just sending signals themselves. Field energy transfer asks can we absorb electromagnetic signals and use its energy? The answer is yes!

Short field energy transfer famously occurs in Radio frequency identification (RFID). RFID tags uses a small radio transmitter and receiver, and when in close proximity to an electromagnetic interrogation pulse, it will be powered and transmit data. The interrogating device typically holds a databased value in order to cross-reference of the data sent by the tag. This allows for supply traceability and identity verification.

When antennas receive a signal, a voltage is generated. Bursts of brodcasts from routers generates enough voltage for a bit under 300mV inconsistently. But, a feature known as poWi-Fi can be used, since routers can simultaneously broadcast across three non-overlapping channels, multiple channels can be used to continually broadcast and remotely power small battery-free devices within 5 meters.

## Resources

1. https://www.daq.net/uploads/file/pdf/DAQ%20DNP3%20Primer.pdf 
2. https://www.ti.com/content/dam/videos/external-videos/en-us/7/3816841626001/6174123090001.mp4/subassets/f2838x_ethercat_introduction.pdf 
3. Sustainable Radio Frequency Solutions by Christina Tucru. 
4. https://www.gs1.org/sites/default/files/docs/epc/uhfc1g2_2_0_0_standard_20131101.pdf  
5. The Internet of Things, 20th Tyrrhenian Workshop on Digital Communications. By Daniel Giusto. 
6. https://www.technologyreview.com/2015/06/03/167817/first-demonstration-of-a-surveillance-camera-powered-by-ordinary-wi-fi-broadcasts/  
7. https://cache.industry.siemens.com/dl/files/306/1172306/att_39239/v1/gsd_e.pdf 
8. https://en.wikipedia.org/wiki/Main_Page
9. https://www.rfwireless-world.com
10. https://www.technologyreview.com/2015/06/03/167817/first-demonstration-of-a-surveillance-camera-powered-by-ordinary-wi-fi-broadcasts/
11. https://www.remoteengineer.eu
