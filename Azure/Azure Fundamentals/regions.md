# Regions, Environments and Availability Zones

## Regions

Regions benefits:
- Data sovereignty in some country.
- Data replication.
- Latency.

Certain regions are paired. Pairings are in the same geopolitical boundary.
Only exception is Brazil South which is paired with South Central US. This is because Brazil
had only one region. But South Central US is not paired with Brazil.

When rolling out updates, they are not applied to the paired regions at the same time.

## Environments

Reasons that different environments exist is law compliance.

There are multiple Azure environments:
- Commercial.
- China - has to be operated by a China company(21vianet).
- US Government(different requirements such as CGS, ITAR).

## Availability Zones

Within regions there are multiple physical buildings. These buildings have independent
power, cooling and communications. These buildings are grouped and exposed as availability zones.

Some regions dont support availability zones. If availability zones are enabled, an azure region contains a minimum of three availability zones

Different subscriptions use different availability zones.

There are different kinds of services from the perspective of availability zones:
- Zone redundant - they span over multiple availability zones automatically.
- Zonal - gets created in a specific availability zone. To have redundancy you have to
create another instance in another availability zone.
