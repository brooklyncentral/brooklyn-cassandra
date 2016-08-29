### HOW TO USE:

Add cassandra-catalog.bom to your AMP catalog.
A new item named "Cassandra cluster" will be available in the Create
Application wizard.
Select it then click "Next". You can specify a location and the configuration
for it in the next page.

Available configuration parameters are:

 - cassandra.archive.url (binary distribution URL)
 - cassandra.cluster.nodes (# of nodes in the cluster)

You can also use the `cassandra-cluster-template` entity directly.
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
  - type: cassandra-cluster-template
    brooklyn.config:
      cassandra.archive.url: 'http://archive.apache.org/dist/cassandra/3.5/apache-cassandra-3.5-bin.tar.gz'
      cassandra.cluster.nodes: 2
```

It will start one node first and use its IP address as a seed for the other nodes.

### KNOWN LIMITATIONS:

*Centos only.* Tested with Centos 7.2.
Only configures `listen_address` and `seeds`.
Uses the defaults for everything else.
