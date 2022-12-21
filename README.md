# Running the MQTT-SN Gateway 


## MQTT-SN Gateway Configuration

	- Modify the BrokerName (i.e IP addr. of mosquitto server) in the "gateway.conf" file present in MQTTSNGateway/bin directory. 
	- To make it compatible with nRF5 SDK example, you have to change UDPv6 Broadcast Address in the "gateway.conf" file present in MQTTSNGateway/bin directory. 


## Running the gateway

	- Run the pre-build gateway present in MQTTSNGateway/bin directory, by executing the "./MQTT-SNGateway" in command line it will use the gateway.conf file as configuration file by default.

