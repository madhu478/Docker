This is the docker swarm 

docker swarm init  { for initializing the docker swarm }
docker swarm join   { this command will appear afterinit command and this command will run on nodes to join the cluster }

Below commands are for docker service 
docker service create --replicas 3 --name [name of the service ] -p 8080:8080 navya3416/jenkins:1.0   { this command is for creating the service }
docker node ls   { for to view the nodes in cluster }
docker swarm leave { to be run on nodes leave the cluster }
docker swarm leave --force { it used when that was last node to leave swarm cluster }
docker service ls { to view the services }
docker service ps [serviceid] { to view details of particular service }
docker inspect [serviceid]
docker service rm [service id or serviename] 
