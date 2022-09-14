#Step1: Configure IP Filtering on Azure IoT hub
After the initial setup, you have one IoT Hub and two device connected and sending telemetry
- the Raspberry Pi simulator online
- the Node device simulation on the Laptop
<br> 
<img width="700" alt="filter1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter1.png">
By default there is no restriction to the IoT Hub public endpoint, <br>
This configuration is at IoT Hub level:
- go to Azure portal, select your IoT Hub,
- select Neworking in the menu,
- the option "all networks" is checked by default
<img width="700" alt="filter3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter3.png">
<br> 

<img width="700" alt="filter2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter2.png">
<br> 
<img width="700" alt="filter4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter4.png">
<br> 
<img width="700" alt="filter5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter5.png">
<br> 
<img width="700" alt="filter6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter6.png">
<br> 

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
