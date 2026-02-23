
# IoT Communication Protocols

> This is just my notes on IoT communication.

## Table of Contents

- [IoT Protocol Stack](#protocol-stack)
- [Communication Ranges](#communication-ranges)
- [High Level IoT Protocols](#high-level-iot-protocols)
- [Transport Layer Considerations](#transport-layer-considerations)
- [Fieldbuses](#fieldbuses)
- [PAN RF Protocols](#pan-rf-protocols)
- [WAN RF Protocols](#wan-rf-protocols)
- [Routing Protocols](#routing-protocols)
- [Middleware](#middleware)
- [Field Energy Transfer](#field-energy-transfer)
- [Resources](#resources)

## Protocol Stack

Typically, IoT protocols can be an TCP/IP stack extension, but the common layers of the OSCI model that IoT protocols work over are as follows:

- **Application Layer** - IoT applications, device management, etc.
- **Transport Layer** - Typically UDP and DTLS
- **Network Layer** - IP routing and IPv6 packets
- **Link Layer** - Traffic and device access

To further dive into this, there's a IoT version of the OSI model stack accoring to source [9]. It's a bit of a stretch, but still a cool model to talk about, and I'm naming it the IoTSI (Internet of Things System Interconnection) model for the purposes of these notes.

1. **Physical Layer** - The communication between the real world and sensors. This uses magic sensor technology that boils down to fancy multimeters.
2. **Processing Layer** - How data gets processed. Microcontrollers and what not.
3. **Hardware Interface Layer** - How hardware talks to each other. CAN, SCI, SPI, I2C, and all that fun stuff. It's the 1s and 0s put onto voltage lines.
4. **RF Layer** - This is where we drop the wires and go into zapping electromagnetic signals across different ranges. This uses Wi-Fi, Bluetooth, Zigbee, Z-Wave, NFC, RFID, GSM, 5G, etc.
5. **Session Layer** - The OSI's application protcols such as MQTT, CoAP, HTTP, SSH, and FTP. It's how messages go to the cloud.
6. **User Experience Layer** - This is where the UI lies and data analytics and interfacing.
7. **Application Layer** - This one is just what the other layers do together and defines the functional system, I guess...

The IoTSI model is more focused on the functionality of the data over how the data transfer actually works, and misses a lot while trying to explain IoT networks.

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

## High Level IoT Protocols

### MQTT (Message Queuing Telemetry Transport)



### HART (Highway Addressable Remote Transducer)



### WebSocket



### CoAP


### AMQP (Advanced Message Queuing Protocol)



### RPC (Remote Procedure Call)



### S7comm



### LwM2M (Lightweight Machine-to-Machine)



### Open Platform Communications (OPC)



### DNP3



## Transport Layer Considerations

## TCP vs. UDP

## Security
- DTLS


## Fieldbuses

Fieldbus is a standardized (IEC 61158) distributed communication network that is designed for real time systems, often utilizing ethernet. Fieldbus relies on connecting multiple devices in often a daisy-chain configuration which collates all devices on a primary bus to the master. IEC 61158 is the standardization of Fieldbus. It outlines required commands and reporting, along with the control scheme. This standardization accounts for a majority of modern Fieldbus protocols. Popular fieldbus protocols include Modbus, Profibus, CANbus, and BACnet [7]. 

### CANBus

Controller Area Network (CAN) Bus is used for communication between electronic control units in vehicles. It is a brodcasting message protocol that is intended to reduce electrical wiring complexity as communication is multiplexed and relies on differential signals. 

### BACnet

BACnet is a protocol for Building Automation and Control (BAC) networks and is typically used for fire detection, lighting, and HVAC systems.

### Profinet



### Modbus



### EtherCAT

EtherCAT (Ethernet for Control Automation Technology) leverages an IEC 61158 Fieldbus system over Ethernet in order to enable real-time computing in industrial applications. Synchronization is expected to be precise and low jitter with less than 1us of clock speed. In this system, an EtherCAT master has a large amount of slaves daisy chained together, and the master communicates with these slaves in a loop style. Typically, the master will have multiple ports connected to the slaves, enabling network redundancy, and have loopback switches that close on failure of the primary communication line, which connects a redundant communication line [2].

## PAN RF Protocols

### Bluetooth 



### BLE



### ZigBee



### Z-Wave




## WAN RF Protocols

### 6LoWPAN



### SigFox




### LoraWAN



## Routing Protocols

Routers route, but IoT routers are special because they route in low power and harsh conditions. Let's talk about that magic.

### RPL (Routing Protocol for Low-Power and Lossy Networks)



### CORPL (Cognitive RPL)



### CARP (Channel Aware Routing Protocol)



### CMSA/CD (Carrier-sense multiple access with collision detection) 



## Middleware

Middleware for IoT networks integrates operating systems and embedded devices. It's primary goal is to take networked embedded devices and provide ambient intelligent application access on machines. Middleware services such as HYDRA enable secure applications for embedded devices, where peer to peer networking can be enabled, and identity management can be handled. Middleware allows for software applications to be significantly easier to develop with middleware that can natively handle embedded devices. Middleware projects and brands includes WhereX, HYDRA, InterDataNet, Z-Wave, and Convergence. Middleware is capable of managing security layers, device management, device locking, and policy enforcement [5].

To go back to the IoTSI model, layer 6 and 7 are possible without middleware, but it's very annoying. Middleware lets random CS kids able to make applications for IoT devices with without them needing to open the datasheets of any of the devices their app uses. It standardizes access between everything.

## Field Energy Transfer

Electromagnetic wave-icles move, which means they have energy. We generate a ton of these regularly, such as ARP broadcasts over Wi-Fi, or even just sending signals themselves. Field energy transfer asks can we absorb electromagnetic signals and use its energy? The answer is yes!

### Short Field Energy Transfer

Short field energy transfer famously occurs in Radio frequency identification (RFID). RFID tags uses a small radio transmitter and receiver, and when in close proximity to an electromagnetic interrogation pulse, it will be powered and transmit data. The interrogating device typically holds a databased value in order to cross-reference of the data sent by the tag [4]. This allows for supply traceability and identity verification [3]

### Long Field Energy Transfer

When antennas receive a signal, a voltage is generated. Bursts of brodcasts from routers generates enough voltage for a bit under 300mV inconsistently. But, a feature known as poWi-Fi can be used, since routers can simultaneously broadcast across three non-overlapping channels, multiple channels can be used to continually broadcast and remotely power small battery-free devices within 5 meters [10].

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
