# Step 3:  Enable Private Endpoint for IoT Hub
For **higher security enforcement** , IoT Hub can grant access  to devices or applications from a private network via a an Azure VNET and block other connections.<br>
This requires the configuration of a Private Endpoint exposed in a VNET with the associated Private Link to an IoT Hub instance.<br<
In this example, with Private Endpoint activated, the Laptop cannot connect to IoT Hub from Internet anymore. <br>
IT means IoT devices or device management applications from Internet are blocked.<br> 
Azure Administrator can still configure Azure IoT Hub through Azure Resource Manager, in order to change Networking configuration for example.<br>

<img width="800" alt="endpoint1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint1.png">
<br>
<img width="700" alt="endpoint2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint2.png">
<br>
<img width="700" alt="endpoint3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint3.png">
<br>
<img width="500" alt="endpoint4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint4.png">
<br>
<img width="500" alt="endpoint5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint5.png">
<br>
<img width="500" alt="endpoint6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint6.png">
<br>
<img width="400" alt="endpoint7" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint7.png">
<br>
<img width="700" alt="endpoint8" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint8.png">
<br>
<img width="700" alt="endpoint9" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint9.png">
<br>
<img width="600" alt="endpoint10" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Endpoint10.png">
<br>

Additional information for Private Endpoints  on Azure documentation : [IoT Hub support for virtual networks with Private Link and Managed Identity](https://docs.microsoft.com/en-us/azure/iot-hub/virtual-network-support)


# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
