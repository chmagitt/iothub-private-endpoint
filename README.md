# Introduction

To help customers secure their IoT Solution from exposure to the Public internet, Azure IoT Hub supports the **Virtual Networks** (VNET pattern).

For **ingress traffic**, the configuration of Azure **Private Link** allows data to flow from IPv4 private addressing networks through Express Route or VPN; it also blocks all other data from Public Internet.

In this document , we will configure an environment where IoT devices and IoT management applications need to connect to IoT Hub with advanced security and we will explore different scenarios:

- Public access
- White listing with IP addresses
- Private IP addresses only
- Jump box scenario

The setup in this Repos can be applied for demo, POC or deployment.

For more details on **IoT Hub support for virtual networks with Private Link and Managed Identity**,  you can read the Microsoft Documentation : [Azure IoT Hub support for virtual networks | Microsoft Docs](https://docs.microsoft.com/en-us/azure/iot-hub/virtual-network-support)


# Network Connectivity Overview (Ingress)
As a short explanation, you can see in the diagram bellow how applications interact with IoT hub.

<img width="823" alt="private-endpoint-intro" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Intro1.png">

Several kinds of applications can communicate with Azure IoT hub: 
- **IoT devices** with embedded applications communicate with IoT Hub using MQTT or AMQP protocols; you may have a couple of devices or millions connected to IoT Hub.<br>
Devices send telemetry and give information of their status to the Cloud (D2C) and they receive messages & commands from the Cloud (C2D) . IoT devices generally rely on Azure IoT **IoT Device SDK** to secure communications and execute IoT Hub features set.<br>

- **IoT device management applications** communicate with IoT Hub using the rest APIs; you may have very few or a lot of device management applications, in a B2C scenario for example.<br>
These applications have access to IoT Hub in order to create, delete, configure, update devices remotely and generally they rely on Azure **IoT Service SDK**.<br>

- **Azure management applications** communicate with Azure **Resource Manager** using the Rest APIs for the configuration of Azure Services including IoT Hub; this connection is dedicated for a limited number of authorized Azure Administrators controlled by Azure AD and RBAC.<br> 
Azure provide many ways for Cloud administration through Portal, CLI, PS Scripts, Arm templates, DevOps tools, etc... all these methods are supported to configure  **IoT Hub features** like, Access Control, Networking, message routing and enrichment, failover, metrics.<br>
>
Both IoT devices and IoT device Management Applications can connect to IoT Hub through a Public or Private Network.<br>
- **Public Network** , in red, is the  way to connect to IoT Hub by default through its public endpoint ; there is also an option to create filters a create a whitelist of IP source address for access restriction.
- **Private Network** , in blue, provides a set of technologies to connect to a VNET (Express route, VPN gateway, ..) and then connect to IoT Hub through its Private Endpoint. This blocks all the connections from Internet for a higher level of security. We will also see later the role of “Jump box” to remotely configure IoT Hub.<br>


# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
