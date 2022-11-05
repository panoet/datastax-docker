# Datastax Docker for easy development
You can use this docker to easy development of Datastax Enterprise

To run:

```docker-compose up```

This will pull 3 image from docker hub:
1. Datastax Server 6.8.4
2. Datastax Studio 6.8.4
3. Datastax OpsCenter 6.8.0

And then install to container with these condition:
- A cluster of Datastax with 1 node
- Using external network named ***datastax*** so additional node possibly added to the cluster
- Datastax running in GRAPH and SEARCH workload

After installation, access studio and opscenter using browser:
- [Studio localhost:9091](localhost:9091)
- [OpsCenter localhost:8888](localhost:8888)

After launching the studio / opscenter, add the seed node using host ```node``` instead of IP address.

## Adding more nodes
```
docker run --network datastax -e DS_LICENSE=accept -e SEEDS=[FIRST NODE IP ADDRESS] -e OPSCENTER_IP=[OPSCENTER IP ADDRESS] --name node2 -d datastax/dse-server:6.8.4 -g -s
```

First, you need to check IP assigned to first node and opscenter using:
```docker inspect [CONTAINER NAME]```

Credits:

[Freemansoft GitHub](https://github.com/freemansoft/docker-scripts)
