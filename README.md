# Build and run the MQTT-SN Gateway 

## Build MQTT-SN Gateway
	
Clone the git repo and checkout the updatedgateway branch.
		
		git clone https://github.com/nikhilkomalan/paho.mqtt-sn.embedded-c.git
		cd paho.mqtt-sn.embedded-c
		git checkout updatedgateway

	- Now move to MQTTSNGateway folder and build the gateway for UDP6 by executing the following command.

		cd MQTTSNGateway
		./build.sh udp6

	- On successfull build, bin folder will be created with the genrated executable files. 	

## MQTT-SN Gateway Configuration

	- Modify the BrokerName (i.e IP addr. of mosquitto server) in the "gateway.conf" file present in MQTTSNGateway/bin directory. 
	
		BrokerName=103.238.13.202 	//Broker address
		BrokerPortNo=1883
		BrokerSecurePortNo=8883

		
	- To make it compatible with nRF5 SDK example, you have to change UDPv6 Broadcast Address in the "gateway.conf" file present in MQTTSNGateway/bin directory. 

		GatewayUDP6Bind=FFFF:FFFE::1 
		GatewayUDP6Port=47193		//Nordic example udp port
		GatewayUDP6Broadcast=ff33:40:fd4f:4166:3f4a:4059:0:1  //OpenThread MLE ID = fd4f:4166:3f4a:4059
		GatewayUDP6If=wpan0
		GatewayUDP6Hops=5		
		
		- Below is the wpan0 interface of my RCP device connected to OTBR (use as reference for setting GatewayUDP6Broadcast
		in above step): 
		
		wpan0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1280
		inet6 fd4f:4166:3f4a:4059:0:ff:fe00:fc38  prefixlen 64  scopeid 0x0<global>
		inet6 fd4f:4166:3f4a:4059:0:ff:fe00:fc10  prefixlen 64  scopeid 0x0<global>
		inet6 fd4f:4166:3f4a:4059:0:ff:fe00:2800  prefixlen 64  scopeid 0x0<global>
		inet6 fe80::a082:e694:6afc:70ce  prefixlen 64  scopeid 0x20<link>
		inet6 fd4f:4166:3f4a:4059:0:ff:fe00:fc00  prefixlen 64  scopeid 0x0<global>
		inet6 fd4f:4166:3f4a:4059:94ca:f193:709f:99c1  prefixlen 64  scopeid 0x0<global>
		inet6 fdf8:d160:b0c:1:c721:668d:fdc3:daa1  prefixlen 64  scopeid 0x0<global>
		inet6 fd4f:4166:3f4a:4059:0:ff:fe00:fc11  prefixlen 64  scopeid 0x0<global>


## Running the gateway

	- Run the pre-build gateway present in MQTTSNGateway/bin directory, by executing the "./MQTT-SNGateway" in command line it will use the gateway.conf file as configuration file by default.


		cd /paho.mqtt-sn.embedded-c/MQTTSNGateway/bin
		./MQTT-SNGateway
