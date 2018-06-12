## Setting up a 3-node Hadoop Cluster

I used [IBM **Cloud** Virtual Servers](https://console.bluemix.net/catalog/infrastructure/virtual-server-group) for setting up the cluster. I spun 3 different servers running _Ubuntu_. I configured the nodes to one master node and two slave nodes, I followed the configuration tutorial here: [How to Install and Set Up a 3-Node Hadoop Cluster](https://www.linode.com/docs/databases/hadoop/how-to-install-and-set-up-hadoop-cluster/). You can use the same approach on any other cloud platform or bare metal servers you have access to. You can also run Hadoop locally on your machine, however, you will not have the benefits of a distributed system and Hadoop will treat your machine as a single node.

IBM **Cloud** has a service that does the same steps followed above for configuration, but provides it for you as an out-of-the-box solution with no setup overhead. The service is called called [**Analytics Engine**](https://console.bluemix.net/catalog/services/analytics-engine). This provides a flexible framework that sets up Hadoop and Spark as well as other related tools on a number of nodes of your choice on the cloud, based on your analytics workload.

Another interesting yet experimental approach is using a Kubernetes cluster of different pods containing data nodes and leveraging volumes for persistent storage. For more ideas on this approach, here's an interesting tech talk from Data Bricks about just that: [HDFS on Kubernetes—Lessons Learned](https://databricks.com/session/hdfs-on-kubernetes-lessons-learned).

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/DxCDxi08HWo/0.jpg)](https://youtu.be/DxCDxi08HWo)
