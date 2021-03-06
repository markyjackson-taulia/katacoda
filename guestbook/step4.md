In this example we'll be running Redis Slaves which will have replicated data from the master. More details of Redis replication can be found at [http://redis.io/topics/replication](http://redis.io/topics/replication)

As previously described, the controller defines how the service runs. In this example we need to determine how the service discovers the other pods. The YAML represents the *GET_HOSTS_FROM* property as DNS. You can change it to use Environment variables in the yaml but this introduces creation-order dependencies as the service needs to be running for the environment variable to be defined.

#### Start Redis Slave Controller

In this case, we'll be launching two instances of the pod using the image _kubernetes/redis-slave:v2_. It will link to _redis-master_ via DNS.

`kubectl create -f redis-slave-controller.yaml`{{execute}}

#### List Replication Controllers

`kubectl get rc`{{execute}}
