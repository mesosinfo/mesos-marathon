mesos-marathon
===========================================================

<a href='https://imagelayers.io/?images=mesosinfo/mesos-marathon:ubuntu-14.04' title='Get your own badge on imagelayers.io'><img src='https://badge.imagelayers.io/mesosinfo/mesos-marathon:ubuntu-14.04.svg'></a>

[![](https://badge.imagelayers.io/mesosinfo/mesos-marathon:ubuntu-14.04.svg)](https://imagelayers.io/?images=mesosinfo/mesos-marathon:ubuntu-14.04 'Get your own badge on imagelayers.io')

Multi-node Setup

For this setup, we will need 3 servers with Docker installed on it.

1. Export out the 3 servers' IP that we will be using on each server

		#zookeeper servers
        ZOOKEEPER_HOST_IP_1=192.168.22.82
        ZOOKEEPER_HOST_IP_2=192.168.22.87
        ZOOKEEPER_HOST_IP_3=192.168.22.92
		 
2. Run the mesos marathon on docker 

    On host #1 (mesos master #1)

		docker run --net="host" \
		-d \
		-p 8080:8080 \
		--master zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		--zk zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/marathon \
		mesosinfo/mesos-marathon

    On host #2 (mesos master #2)

		docker run --net="host" \
		-d \
		-p 8080:8080 \
		--master zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		--zk zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/marathon \
		mesosinfo/mesos-marathon

    On host #3 (mesos master #3)

		docker run --net="host" \
		-d \
		-p 8080:8080 \
		--master zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		--zk zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/marathon \
		mesosinfo/mesos-marathon
	
