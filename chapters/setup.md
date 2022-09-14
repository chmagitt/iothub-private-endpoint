# Environment setup


In order to connect and test different scenario with IoT Hub Private Endpoint, four components are necessary

- **A laptop** (or VM) connected to Internet; in this machine some device simulations and device management applications are required to connect to IoT Hub. The VPN client will provide the Private Network connectivity using an Ipsec tunnel.
- **An IoT Hub** instance that devices and application will try to connect to.
- **An Azure VPN gateway** to connect VPN client and then create a private network over Internet.
- **A Windows VM** to act as a Jump Box , connected to the same Vnet as IoT Hub Private Endpoint.


<img width="823" alt="private-endpoint-intro" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Setup1.png">


# Prepare the environment

For this setup, you need at least an **IoT Hub** , a **Windows VM on Azure**, a Laptop with a **device simulation** and the **VPN client** 

## IoT Hub
Install Azure IoT in your subscription.<br>
Follow the Quick Start in Azure Documentation for [IoT Hub Creation](https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-send-telemetry-iot-hub)

## Node JS device simulation (Laptop)
This application on the Laptop will be white listed, then blocked  then  connected through the VPN gateway to IoT Hub. <br>
You need to install [NodeJs](https://nodejs.org/en/download/). <br>
Follow the Quick Start in Azure Documentation to [Send telemetry to IoT Hub](https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-send-telemetry-iot-hub?pivots=programming-language-nodejs)

## VPN client (Laptop)
Download the latest version of the Azure VPN Client install files using one of the following links:<br>
Install using Client Install files: https://aka.ms/azvpnclientdownload.<br>
Install directly, when signed in on a client computer: [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=2117554)

## Azure IoT Edge (Laptop) - it is optionnal
This requires to run a EFLOW VM on the Laptop if you want to also test IoT Edge in addition to Azure IoT SDK<br>
Follow the [IoT Edge on Windows installation Guide](https://docs.microsoft.com/en-us/azure/iot-edge/quickstart?view=iotedge-1.4)<br>
You don't need to deploy module, we can check the connectivity status with IoT Edge without sending data.

## Azure VM - Windows 10 or 11
You need a Windows VM for the Jumpbox.<br>
It can be an existing WM as you don't need to install any application and you just need a couple of IP address in the VM VNET for 2 private endpoints and VPN gateway.<br>
For a new VM, you can follow this Quick Start guide: [Create a Windows virtual machine in the Azure portal](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal).

## Rapsberry Pi Online simulator
This application will creat a second IoT device to show the IP filtering capabilities of IoT hub. <br>
Follow the "how-to guide" to [connect RPI simulator](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started)
<br>
<br>

# Setup and Scenarios

- [Introduction](https://github.com/chmagitt/iothub-private-endpoint#readme)
- [Step1](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/setup.md): Initial Setup
- [Step2](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/ipfilter.md): Filter Ip Source addresses.
- [Step3](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/endpoint.md): Allow only Private Networks with Private Endpoint.
- [Step4](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/jumpbox.md): Device Management through a Jump Box.
- [Step5](https://github.com/chmagitt/iothub-private-endpoint/blob/main/chapters/vpngateway.md): Iot Device connected to IoT Hub through a VPN.
