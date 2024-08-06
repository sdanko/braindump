# Storage Accounts

It lives in a specific region. When creating a storage account you pick which kind of resiliency you want.
Replication is always asynchronous.

## LRS

There are always 3 copies of the data, but those 3 copies are within the sane cluster. 
They are in the same data center.

## Zone Redundant(ZRS)

There are also 3 copies, but they are located in 3 different availability zones.

## GRS

There are 3 copies in the same datacenter and there are 3 copies in a paired region(also in the same datacenter).

## GZRS

There are 3 copies in 3 different availability zones and there are 3 copies in a paired region, but in the same datacenter.

## Performance

There are different performance options:
- Standard
- Premium(there is no geo replicated option)

## Blobs

- Block
- Page
- Append

Container are flat and have no directory structure.

## Disks

Disk are using page blobs in the background.

Types:
- Standard
- Standard SSD
- Premium SSD 
- Ultra

With Standard and Premium types, the performance scales linearly with the amount
of capacity you add.

To be able to use Premium SSD adn Ultra disks on the virtual machine, it has to be 
the S variant of the virtual machine.

## Files

Gives an option to have SMB or NFS shares.

Azure File Sync synchronizes on premise file servers to the Azure file share.

## Queues

These are small messages in FIFO format. Normally used to drive some event driven process.

## Tables

It is a key value storage without data scheme.

## Access Tiers

- Hot - you pay more money for the storage but less for the transactions.
- Cool - you pay less money for the storage but more for the transactions.
- Archive - it is offline and has to be moved to hot or cool tier to access data.

With Lifecycle Management you can set rules when the data will be moved to different tiers.
