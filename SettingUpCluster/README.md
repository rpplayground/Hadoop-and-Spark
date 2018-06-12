## Setting up a 3-node Hadoop Cluster

I used [IBM **Cloud** Virtual Servers](https://console.bluemix.net/catalog/infrastructure/virtual-server-group) for setting up the cluster. I spun 3 different servers running _Ubuntu_. I configured the nodes to one master node and two slave nodes, I followed the configuration tutorial here: [How to Install and Set Up a 3-Node Hadoop Cluster](https://www.linode.com/docs/databases/hadoop/how-to-install-and-set-up-hadoop-cluster/).

IBM **Cloud** has a service that does the same for you out-of-the-box called [**Analytics Engine**](https://console.bluemix.net/catalog/services/analytics-engine). This provides a flexible framework that sets up Hadoop and Spark as well as other related tools on a number of nodes of your choice, based on your analytics workload.
