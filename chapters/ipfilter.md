# Step1: Configure IP Filtering on Azure IoT hub
## IoT Hub default configuration
After the initial setup, you have one IoT Hub and two devices connected, sending telemetry
- the Raspberry Pi simulator online
- the Node device simulation on the Laptop
<br> 
<img width="900" alt="filter1" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter1.png">
By default there is no restriction to the IoT Hub public endpoint,<br>
This configuration is at IoT Hub level

- Go to Azure portal, select your IoT Hub
- Select Neworking in the menu
- Option "all networks" is checked by default
<img width="700" alt="filter3" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter3.png">
<br> 

## IP filter configuration
In order restrict the access to Iot Hub  you can allow only some devices or some application<br>
In this example, the Raspverry Pi online will be blocked<br>
<br> 
<img width="850" alt="filter2" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter2.png">
<br> 
For this configuration, you need to stay on "Networking" menu of IoT Hub

- Check the option "Selected IP range"
- By default Azure Portal detecte the IP of you Laptop
- You can keep this IP, change it or add new IP
- "Save"
<img width="700" alt="filter4" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter4.png">
<br> 
In the screenshots bellow we can notice that the connection from the laptop to IoT hub is up and running

- Azure Portal give access to the list of device
- VS Code cane connect to IoT Hub via Rest API
- Device Simulation send telemetry
- Azure IoT Edge is connected
<img width="700" alt="filter5" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter5.png">
<br> 
<img width="700" alt="filter6" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Filter6.png">
<br> 

Additional information for IP Filtering on Azure documentation : [Use IP filter](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-ip-filtering)

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
