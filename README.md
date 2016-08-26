### HOW TO USE:

Add cassandra-catalog.bom to your AMP catalog, then you can use
the `cassandra-cluster` entity in your application.

For example, use this blueprint to deploy a cluster to Blue Box:

```
name: Cassandra Cluster on Blue Box (LON)

location:
  ibm-bluebox-lon-vpn:
    osFamily: centos
    minRam: 1gb
    installDevUrandom: true
    loginUser: centos

services:
- type: cassandra-cluster
  initialSize: 2
```

It will start one node first and use its IP address as a seed for the other nodes.

### KNOWN LIMITATIONS:

Centos only. Tested with Centos 7.2.
Fixed download URL (change it in the catalog entry)
Only configures `listen_address` and `seeds`.
Uses the defaults for everything else.
