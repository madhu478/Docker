This is the docker swarm 

docker swarm init  { for initializing the docker swarm }

docker swarm join   { this command will appear afterinit command and this command will run on nodes to join the cluster }

Below commands are for docker service 

docker service create --replicas 3 --name [name of the service ] -p 8080:8080
navya3416/jenkins:1.0   { this command is for creating the service }


docker node ls   { for to view the nodes in cluster }


docker swarm leave { to be run on nodes leave the cluster }


docker swarm leave --force { it used when that was last node to leave swarm cluster }


docker service ls { to view the services }


docker service ps [serviceid] { to view details of particular service }


docker inspect [serviceid]


docker service rm [service id or serviename] 


# this is for scaliong the services

docker service scale [servicename ]=[up or down replicas by giving the number ]  


docker node update --availability drain [nodename]  { drain all services running on particular node }


docker node update --availability active [nodename]


if we add the new node it can br assigned to service automatically by using --mode global


# Docker Rolling updates

upgrade a service in Docker using rolling updates 
serice really is just an application that's been served up by muliple docker swarm nodes so we have high availabiltiy and load balncing. so update the some aspect of application so image also updated and with zero downtime we use that image in service


docker servvice inspect --pretty [servicename] 

docker service update --image navay3416/jenkins:2.0  [service name]



# Docker secrets 
sensitive info certificates or passwords those kind info stored in docker secrets 

This docker secret notation works with docker service not to docker container running on standalone dockerhost


docker secret create [namecreds] [where it is coming from (file name) in the same directory]
docker secret ls 
docker service create --replicas 3 --secret appcreds -p 8080:8080  --name corpwebsite [image] 


docker container exec $(docker ps --filter name=corpwebsite -q) ls -l /run/secrets


docker container exec $(docker ps --filter name=corpwebsite -q) cat /run/secrets


# Docker config 
 
Docker swarm config is a configuration set that we can aply when we start a docker swarm service and it colud be done for just about anything such as making changes to files in the file system within a conatianer or maybe changing a config file which will be doing our example 

what this do is it lets us keep some configuration settings outside of docker images used for container


that config file will be into running container 

docker config create apacheports ports.conf


docker config ls

docker config ipspect --pretty apacheports

docker service create --replicas 3 -p 8080:8080 --nbame corpwebsite --config source=apacheports,target=/etc/apache2/ports.conf,mode=0440 [image]
