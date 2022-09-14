# Step 4: Connect a Latop to the Jumpbox for Device Management
In the previous steps, the Private Endpoint prevents IoT device and Device Management application to connect to IoT from Internet.<br>
But if business requirements need to configure device from some specific machines outside IoT Hub VNET, then it is possible to connect to an Azure VM with RDP protocol, then open a device management application on this VM <br>
In this configuration, there is no direct connection from Internet to Iot Hub: 
- **NSG (Network Security Group)** role is to  filter ingress connection from Internet to the Jump Box VM
- **VNET (Virtual Network)** provides the network connectivity between the Jump Box and IoT Hub
- **Private DNS zone** answers to name resolution requests in the VNET to reach IoT hub
<br> 
<img width="800" alt="jump1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Jump1.png">
<br>
The diagram bellow explains how Private DNS zone works.<br>
In our configuration the Jumpbox sends a DNS query for **iothub-xyz.azure-devices.net**  to Azure Global DNS, expecting IoT Hub public IP and  finally Private DNS zone resolve the  **iothub-xyz.privatelink.azure-devices.net** name and sends the private IP of IoT Hub to the Jump Box.
  
More details on Private DNS zone in the documentation: (https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-dns#virtual-network-workloads-without-custom-dns-server)
<img width=500" alt="jump2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Jump2.png">
<br>
<img width="800" alt="jump3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Jump3.png">
<br>
<img width="800" alt="jump4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Jump4.png">
<br>
<br>

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
