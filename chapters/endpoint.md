# Step 3:  Enable Private Endpoint for IoT Hub
For **higher security enforcement** , IoT Hub can grant access  to devices or applications from a private network via a an Azure VNET and block other connections.<br>
This requires the configuration of a Private Endpoint exposed in a VNET with the associated Private Link to an IoT Hub instance.<br>
<br>
In the example bellow, with Private Endpoint activated, the Laptop cannot connect to IoT Hub from Internet anymore so  IoT device simulation and device management applications are out of order .<br> 
At the same time, it is still possible for the Laptop to configure IoT Hub via Azure Resource Manager.<br>

<img width="800" alt="endpoint1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint1.png">
<br>

## Create a Private endpoint
- Go to Azure portal, select your IoT Hub
- Select Neworking in the menu
- Check the option "Disable" for Public network access <br>
- Select "Private access"
- Then "Create a private endpoint"
<img width="800" alt="endpoint2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint2.png">
<br> 
<img width="800" alt="endpoint3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint3.png">
<br> 
This will trigger the configuration of Private Endpoint in 6 Steps

- choose a name for the Endpoint, it proposes a name for the Network Interface
- target sub-resource is iot-hub
- choose the **same Virtual Network as your W10 VM** which will play the role of Jump Box
- the two DNS name will be the new FQDN of IoT Hub and egress Service Bus in the VNET
- check your configuration and "Create"
<br> 

<img width="600" alt="endpoint4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint4.png">
<br> 
<img width="600" alt="endpoint11" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint11.png">
<br> 
<img width="600" alt="endpoint5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint5.png">
<br> 
<img width="600" alt="endpoint6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint6.png">
<br> 
<img width="500" alt="endpoint7" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint7.png">
<br> 
## Check the configuration

At the end of the configuration the "Private access" page of IoT Hub shows the new Private Endpoint.<br>
When you click on the Endpoint you can watch the "DNS configuration" showing the  new Network Interface connected to the VNET and the two new **private IP addresses** (10.2.1.36 and 10.2.1.37) dynamically allocated in the subnet you have chosen in the previous steps and their associated **private FQDN** (privatelink)  .<br>
<br> 
<img width="800" alt="endpoint8" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint8.png">
<br>
<img width="800" alt="endpoint9" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint9.png">
<br>
##Test

Finaly, with this new Private Endpoint, Internet traffic is blocked and the Laptop cannot access to IoT Hub for device telemetry or device management.<br>
For example the Laptop cannot manage devices from Azure Portal; the menu "Devices" in IoT Hub cannot show the list of the devices and it is not possible to send messages or update device twins.<br>
<br> 
<img width="700" alt="endpoint10" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint10.png">
<br>

Additional information for Private Endpoints  on Azure documentation : [IoT Hub support for virtual networks with Private Link and Managed Identity](https://docs.microsoft.com/en-us/azure/iot-hub/virtual-network-support)


# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
