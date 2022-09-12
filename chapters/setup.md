# Initial Setup


In order to connect and test different scenario with IoT Hub Private Endpoint, four components are necessary

- A laptop (or VM) connected to Internet; in this machine some device simulations and device management applications are required to connect to IoT Hub. The VPN client will provide the Private Network connectivity using an Ipsec tunnel.
- An IoT Hub 
- An Azure VPN gateway to connect VPN client
- A Windows VM to act as a Jump Box , connected to the same Vnet as IoT Hub Private Endpoint/


<img width="823" alt="private-endpoint-intro" src="https://github.com/chmagitt/iothub-private-endpoint/blob/main/media/Setup1.png">
