# Introduction

To help customers secure their IoT Solution from exposure to the Public internet, Azure IoT Hub supports the **Virtual Networks** (VNET pattern).

For ingress traffic, the configuration of Azure **Private Link** allows data to flow from IPv4 private addressing networks through Express Route or VPN; it also blocks all other data from Public Internet.

In this document , we will configure an environment where IoT devices and IoT management applications need to connect to IoT Hub with advanced security and we will explore different scenarios:

- Public access
- White listing with IP addresses
- Private IP addresses only
- Jump box scenario

The setup proposed in this Repos can be applied for demo, POC or deployment.

For more details on **IoT Hub support for virtual networks with Private Link and Managed Identity**,  you can read the Microsoft Documentation : [Azure IoT Hub support for virtual networks | Microsoft Docs](https://docs.microsoft.com/en-us/azure/iot-hub/virtual-network-support)


# Network Connectivity Overview (Ingress)
As a short explanation, you can see in the diagram bellow how applications interact with IoT hub.

<img width="823" alt="private-endpoint-intro" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Intro1.png">

Several applications can communicate with Azure IoT hub: 
- **IoT devices** with embedded applications communicate with IoT Hub using MQTT or AMQP protocols
> Devices send telemetry and give information of their status to the Cloud and they receive messages & commands from the Cloud. IoT devices generally rely on Azure IoT Device SDK to secure communications and execute IoT Hub features set.

- **IoT devices management applications** communicate with IoT Hub using the rest APIs 
> in order to configure the device registry and interact with these devices through device twins, methods and messages. These applications generally rely on Azure IoT Service SDK.

- **Azure IoT Hub management applications** communicate with Azure Resource Manager using the Rest APIs
> This can be Azure Portal, CLI, PS Scripts, Arm templates, DevOps tools, … This allows end-users to configure all Azure IoT Hub features not related to Device Management like Networking, message routing and enrichment, failover, metrics.
<br>
<br>
Both IoT devices and IoT device Management Applications can connect to IoT Hub through a Public or Private Network.

- **Public Network**: in red, this is the legacy way to connect to IoT Hub through its public endpoint ; there is also an option to filter a whitelist of IP source address for access restriction.

- **Private Network**: in blue, it provides a set of technologies to connect to a VNET (Express route, VPN gateway, ..) and then connect to IoT Hub through its Private Endpoint. This blocks all the connections from Internet for a higher level of security. We will also see later the role of “Jump box” to remotely configure IoT Hub.
<br>
<br>

# Setup and Scenarios

- Back to [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
