# Running the MQTT-SN Gateway 


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

## Running the gateway

	- Run the pre-build gateway present in MQTTSNGateway/bin directory, by executing the "./MQTT-SNGateway" in command line it will use the gateway.conf file as configuration file by default.

