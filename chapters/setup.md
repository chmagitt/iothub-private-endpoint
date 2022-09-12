# Environment setup


In order to connect and test different scenario with IoT Hub Private Endpoint, four components are necessary

- **A laptop** (or VM) connected to Internet; in this machine some device simulations and device management applications are required to connect to IoT Hub. The VPN client will provide the Private Network connectivity using an Ipsec tunnel.
- **An IoT Hub** instance  
- **An Azure VPN gateway** to connect VPN client
- **A Windows VM** to act as a Jump Box , connected to the same Vnet as IoT Hub Private Endpoint/


<img width="823" alt="private-endpoint-intro" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Setup1.png">


# Prepare the environment

## IoT Hub
Install Azure IoT in your subscription.<br>
Follow the Quick Start in Azure Documentation for [IoT Hub Creation](https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-send-telemetry-iot-hub)

## Node JS device simulation
This application on the Laptop will be white listed, then blocked  then  connected through the VPN gateway to IoT Hub. <br>
You need to install [NodeJs](https://nodejs.org/en/download/). <br>
Follow the Quick Start in Azure Documentation to [Send telemetry to IoT Hub](https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-send-telemetry-iot-hub?pivots=programming-language-nodejs)

## Rapsberry Pi Online simulator
This application will creat a second IoT device to show the IP filtering capabilities of IoT hub. <br>
Follow the "how-to guide" to [connect RPI simulator](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started)

## Azure IoT Edge (Optional)
This requires to run a EFLOW VM on the Laptop if you want to also test IoT Edge in addition to Azure IoT SDK<br>
Follow the [IoT Edge on Windows installation Guide](https://docs.microsoft.com/en-us/azure/iot-edge/quickstart?view=iotedge-1.4)<br>
You don't need to deploy module, we can check the connectivity status with IoT Edge without sending data.
