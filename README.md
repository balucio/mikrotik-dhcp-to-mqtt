# mikrotik-dhcp-to-mqtt
Publish Mikrotik DHCP Lease on MQTT topic using the Mikrotik IOT Package

1. Install IOT Package
2. Configure your broker using Winbox or `/iot mqtt brokers` command
3. Import the scrip
4. Edit line 87 and set your broker name 
   :local mqttBrokerName "mqtt-broker"; # Name sets in /iot mqtt brokers
5. Set the name of the event script in DHCP Server `lease-script` param


This script will publish on the MQTT topic 

`dhcp/<event_type>/<leaseMAC>` the following json data
```
{
  "mac": <MAC address>,
  "ip" : <IPv4>,
  "event_type: {add|del},
  "lease_duration_seconds": <Lease duration in seconds>
}
```
