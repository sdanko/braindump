# Azure Networking

## Virtual Network

Virtual Network cannot span across multiple regions or subscriptions. They span availability zones.

It is defined by a group of minimum IP v4 address ranges.

You can optionally add IP v6 address ranges.

You can create virtual subnets. For every subnet created you lose 5 addresses.

You can peer multiple networks, but IP addresses need to be unique.

## Gateway

Gateway device on Azure establishes a tunnel with an on-premise gateway device. 

This kind of setup support point to site connections, which means you can connect a particular machine to the gateway.
The connection is going over the internet, but it is encrypted.


## ExpressRoute Gateway

This is a private connection that is not going over the internet.

It can be a layer 3 or layer 2 connection.

## Network Security Group

It is built around the following properties:
- Source/Destination IP range
- Source/Destination port
- Protocol
- Name/Description/Priority
- Allow/Deny

Network Security Groups are linked to subnets.

## Azure Firewall

It understands layer 4, but it also understands layer 7(application rules). It supports DNAT.

To plug in the Azure Firewall, you use User Defined Routes.

## Service Endpoint

It connects a virtual network subnet to a service. It can be used with a service firewall.

There are also private endpoints which represent an IP address that is connected to a certain version of a service.

## DDoS Protection

Two offerings:
- Basic protection
- Standard protection(can be linked to multiple virtual networks)