# Step 5: Connection to IoT Hub from a VPN gateway
In the Previous step, the Jump Box is a workaround to provide device management capabilities for Internet users via RDP protocol.<br>
But this is not a solution to connect IoT Devices which need direct connection to IoT Hub.<br>
In this scenario, an Azure Expressroute or VPN gateway is necessary to connect devices to Private Endpoint VNET.<br>
The example bellow shows our configuration with **Point-to-Site VPN** : a Latop connected to the IoT Hub Private Endpoint VNET via an IPSEC tunnel.<br>
This setup gives full access to  IoT Hub for device telemetry and  device management.

<img width="800" alt="vpngateway1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw1.png">
<br>

## Installation of a VPN gateway

### Create the Gateway

- Go to Azure Portal
- Search  "virtual network gateway " in Azure ressources
- "Create"
- Same Region as the IoT Hub and VNET
- Generation: Gen2
- Virtual network must be the **same Vnet as IoT Hub Private Endpoint**
- "Create"
It can take time for provisioning<br>

### Configure the security credentials of the VPN gateway

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

More details for Point-to-Site VPN in Microsoft documentation[Create a Site-to-Site connection using the Azure portal](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-classic-portal)  

## Connect VPN client

- Download the VPN client from VPN Gateway configuration page in  Azure Portal 
- Launch the VPN client and choose the downloaded file to automatic fill client settings
- Choose the Azure VPN  gateway in the list of VPN servers
- Connect
- You can check the VPN client and the VPN gateway connection prperties 

<img width="300" alt="vpngateway4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw4.png">
<br>
<img width="300" alt="vpngateway5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw5.png">
<br>
<img width="800" alt="vpngateway6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw6.png">
<br> 
## DNS configuration on the Laptop

When the VPN tunnel is up and running, the Laptop cannot connect to IoT Hub as it needs to resolve iothub-xyz.azure-devices.net (public FQDN of IoT Hub).<br>
<img width="800" alt="vpngateway9" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw9.png">
<br>
This can be done wiht Private DNS Zone and a DNS Forwarder (Linux machine)  but in our example we will edit the hosts file of the Laptop so the DNS resolution is hard coded in the OS .
  
- Run Notpad  as Administrator
- Open  file : browse host file folder C:\Windows\System32\drivers\etc
- Open the file "hosts"
- Add an entry with the pair: private IP of Iot Hub   public FQDN of IoT Hub 
<img width="800" alt="vpngateway7" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw7.png">
<br>
With this configuration the Laptop can connect to IoT Hub
- The device simulation send telemetry
- The Device management application in AZure Portal can edit the list of devices
<br>
<img width="800" alt="vpngateway8" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Vpngw8.png">
<br>
<br>

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
