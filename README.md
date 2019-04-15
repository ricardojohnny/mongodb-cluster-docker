# mongo-cluster-docker
# Run

```
docker-compose -f docker-compose.1.yml -f docker-compose.2.yml  -f docker-compose.cnf.yml -f docker-compose.shard.yml up
```

# Testes
> Manual
0. Core tests

Basico *replica* teste no *rs1* replicaset, `mongo-1-1`
```js
rs.status();
```
Basico *sharding* teste no *router* (mongos), `mongo-router`
```js
sh.status();
```

tem que retornar algo similar a isso: 

```
--- Sharding Status --- 
  sharding version: {
	"_id" : 1,
	"minCompatibleVersion" : 5,
	"currentVersion" : 6,
	"clusterId" : ObjectId("587d306454828b89adaca524")
}
  shards:
  active mongoses:
	"3.4.1" : 1
  balancer:
	Currently enabled:  yes
	Currently running:  yes
		Balancer lock taken at Mon Jan 16 2017 22:18:53 GMT+0100 by ConfigServer:Balancer
	Failed balancer rounds in last 5 attempts:  0
	Migration Results for the last 24 hours: 
		No recent migrations
  databases:

```

```
docker-compose -f docker-compose.1.yml -f docker-compose.2.yml  -f docker-compose.cnf.yml -f docker-compose.shard.yml rm -f
```
