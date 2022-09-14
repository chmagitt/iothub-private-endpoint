# Step 5: Connection to IoT Hub from a VPN gateway
In the Previous step, the Jump Box is a workaround to provide device management capabilities for Internet users via RDP protocol.<br>
But this is not a solution to connect IoT Devices which need direct connection to IoT Hub.<br>
In this scenario, an Azure Expressroute or VPN gateway is necessary to connect devices to Private Endpoint VNET.<br>
The example bellow shows our configuration with a Latop connected to the IoT Hub Private Endpoint VNET via an IPSEC tunel.<br>
This setup gives full access to  IoT Hub for device telemetry and  device management.<br>

<img width="800" alt="vpngateway1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw1.png">
<br>
## Installation of a VPN gateway

- Go to Azure Portal
- Search  "virtual network gateway" in Azure ressources
- Add and configure the gateway 
- Address pool can be any network
- Choose "OpenVPN(SSL)" tunnel type and "AAD" Authentication type
- Tenant:https://login.microsoftonline.com/<tenant-id>
- Audience:41b23e61-6c1e-4545-b367-cd054e0ed4b4
- Issuer:https://sts.windows.net/<tenant-id>/
<br>
<img width="700" alt="vpngateway2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw2.png">
<br>
<img width="700" alt="vpngateway3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw3.png">
<br>

## Connect VPN client
You can check the VPN client settings and the VPN gateway 

<img width="300" alt="vpngateway4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw4.png">
<br>
<img width="300" alt="vpngateway5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw5.png">
<br>
  
## DNS configuration on the Laptop
  
<img width="800" alt="vpngateway6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw6.png">
<br>
<img width="800" alt="vpngateway7" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw7.png">
<br>
<img width="800" alt="vpngateway8" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw8.png">
<br>
<img width="800" alt="vpngateway9" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw9.png">
<br>
<br>

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
