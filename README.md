# docker-mastery
Learn Docker and Devops. Docker Mastery: The Complete Toolset From a Docker Captain.

Docker Mastery: The Complete Toolset From a Docker Captain  
https://www.udemy.com/docker-mastery

Course Resource
* [Docker_CheatSheet](https://github.com/smalltide/docker-mastery/blob/master/resource/cheatsheet.pdf)  
* [Slides1-5](https://github.com/smalltide/docker-mastery/blob/master/resource/Slides1-5.pdf)  
* [Slides6-10](https://github.com/smalltide/docker-mastery/blob/master/resource/Slides6-10.pdf)  
* [Play with Docker Classroom](http://training.play-with-docker.com)  
* [awesome-docker](https://github.com/veggiemonk/awesome-docker)  

Skills
1. Docker
2. DevOps
3. Docker Compose
4. Docker Swarm
5. Docker Machine
6. GitHub
7. DockerHub

Bonus Lecture
```
  > https://www.youtube.com/watch?v=ZdUcKtg84T8 (Journey to Docker Production)
  > https://www.youtube.com/watch?v=Qsv-q8WbIZY (Everything You Thought You Already Knew About Orchestration)
  > https://www.youtube.com/watch?v=_4QzP7uwtvI (Docker tip: docker system prune and df)
  > https://www.youtube.com/watch?v=-NeaXUGEK_g (Docker 17.06 Community Edition)
```

install docker bash completion on Mac
```
  > https://docs.docker.com/docker-for-mac/#installing-bash-completion
  > brew install bash-completion
  > ln -s /Applications/Docker.app/Contents/Resources/etc/docker.bash-completion /usr/local/etc/bash_completion.d/docker
  ln -s /Applications/Docker.app/Contents/Resources/etc/docker-machine.bash-completion /usr/local/etc/bash_completion.d/docker-machine
  ln -s /Applications/Docker.app/Contents/Resources/etc/docker-compose.bash-completion /usr/local/etc/bash_completion.d/docker-compose
```
install docker, docker-machine, docker-compose in Linux
```
  > https://store.docker.com
  > https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/
  > curl -sSL https://get.docker.com/ | sh (install latest docker using script)
  > docker version
  > sudo usermod -aG docker <linux user> (add user in docker group)
  > curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine && chmod +x /tmp/docker-machine && sudo cp /tmp/docker-machine /usr/local/bin/docker-machine (install docker machine)
  > docker-machine version
  > sudo -i
  > sudo curl -L 
  https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose (install docker compose)
  > chmod +x /usr/local/bin/docker-compose
  > exit
  > docker-compose version  
```
start a nginx web server container
```
  > docker container run --publish 80:80 nginx (--publish for port, -p)
  > docker container run --publish 80:80 --detach nginx (--detach for run in background, -d)
  > curl 127.0.0.1
  > docker container ls
  > docker container stop <container id>
  > docker container ls -a
  > docker container run --publish 80:80 --detach --name webhost nginx (--name for define container name)
  > docker container logs webhost (watch log in webhost container)
  > docker container top webhost (watch process in webhost container)
  > docker container --help
  > docker container rm <container id> (docker container rm 4d5 834 9bc)
  > docker container rm -f <container id> (force delete docker container
```
Container VS. VM: It's Just a Process
```
  > docker container run --name mongo -d mongo
  > docker container top mongo
  > ps aux (show all running process)
  > ps aux | grep mongo
  > docker container stop mongo
  > ps aux | grep mongo
  > docker container start mongo
  > ps aux | grep mongo
```
Some docker container supply resource
```
  > https://github.com/mikegcoleman/docker101/blob/master/Docker_eBook_Jan_2017.pdf
  > https://www.youtube.com/watch?v=sK5i-N34im8 (Cgroups, namespaces, and beyond: what are containers made from?)
  > https://www.youtube.com/watch?v=066-9yw8-7c (Windows Containers and Docker 101)
  > https://www.youtube.com/watch?v=4ZY_4OeyJsw (Windows and Linux Parity with Docker)
  > https://www.youtube.com/watch?v=QASAqcuuzgI (Docker + Microsoft - Investing in the Future of your Applications)
```
Manage Multiple Containers
```
  > docker container run --name nginx -p 80:80 -d nginx
  > docker container run --name httpd -p 8080:80 -d httpd
  > docker container run --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=yes -p 3306:3306 -d mysql
  > docker container logs mysql (find the root pwd in mysql log)
  > docker container stop nginx httpd mysql
  > docker container rm nginx httpd mysql
  > docker container <stop, or rm> <container id, or name >
  > docker container ls
```
Containers CLI Process Monitoring
```
  > docker container run --name nginx -p 80:80 -d nginx
  > docker container run --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=yes -p 3306:3306 -d mysql
  > docker container top mysql
  > docker container inspect mysql
  > docker container stats (realtime monitor container stat) 
```
Run Shell Inside Containers
```
  > docker container run -it <image> (start a interactive container)
  > docker container exec <container> <command> (run command in container)
  > docker container run -it --name proxy nginx bash
  > ls -al (in container now)
  > docker container ls -a
  > docker container start -ai proxy
  > ls -al (in container now)
  > docker container exec <container> <command> (ex. ip a)
  > docker container exec mysql ip a
  > docker container exec -it <container> <command> (ex. bash)
  > docker container exec -it mysql bash
  > ps aux (in container now)
  > docker pull alpine
  > docker container run -it alpine sh
```
Linux Package Management Basics: apt, yum, dnf, pkg
```
  > https://www.digitalocean.com/community/tutorials/package-management-basics-apt-yum-dnf-pkg
```
Docker Networks and Container and command
```
  > docker container port <container> (watch container using port)
  > docker container run -p 80:80 --name webhost -d nginx
  > docker container port webhost
  > docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhos (foramt to Go template)
  > docker network ls
  > docker network inspect bridge
  > docker network create --driver=bridge my_app_net
  > docker network inspect my_app_net
  > docker network create --help
  > docker container run -d --name new_nginx --network my_app_net nginx
  > docker network inspect my_app_net
  > docker network connect my_app_net webhost (add webhost in my_app_net network)
  > docker container inspect webhost
  > docker network disconnect my_app_net webhost (remove webhost in my_app_net network)
  > docker container inspect webhost
```
Docker Networks: DNS and How Containers Find Each Other
```
  > docker container ls
  > docker container run -d -p 80:80 --name nginx1 --network my_app_net nginx:alpine
  > docker container run -d --name nginx2 --network my_app_net nginx:alpine
  > docker container run -d --name nginx3 --network my_app_net nginx:alpine
  > docker container exec -it nginx1 ping nginx2 (reach)
  > docker container exec -it nginx2 ping nginx3 (reach)
  > docker container run -d --name nginx4 nginx:alpine
  > docker container run -d --name nginx5 nginx:alpine
  > docker container exec -it nginx4 ping nginx5 (no reach, because default bridge network no build-in DNS)
```
Using Containers to test different Linux CLI
```
  > docker container run --rm -it centos:7 bash (--rm, mean delete container when exit)
  > curl version (in container now)
  > docker container run --rm -it ubuntu:14.04 bash (--rm, mean delete container when exit)
  > curl version (in container now)
```
DNS Round Robin Test, use --network-alias
```
  > docker network create dude
  > docker container run -d --network dude --network-alias web httpd
  > docker container run -d --network dude --network-alias web nginx
  > docker container ls (see 2 web server run on 80 port)
  > docker container run --rm --network dude alpine nslookup web (Address 1: 172.19.0.2 web.dude, Address 2: 172.19.0.3 web.dude)
  > docker container run --rm --network dude alpine ping web (run many times, and response 172.19.0.2 or 172.19.0.3 randomly)
```
Using Docker Hub Registry Images
```
  > docker pull nginx (image name)
  > docker pull nginx:1.11.9 (image name and version)
  > docker image ls
```
Images and Their Layers
```
  > docker image history nginx (nginx image build layers)
  > docker image history mysql (mysql image build layers)
  > docker image inspect nginx 
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/image-layer.png "image-layer")

Image Tagging and Pushing to Docker Hub
```
  > docker image tag <source image:tag> <target image:tag>
  > docker image tag alpine smalltides/alpine
  > cat ~/.docker/config.json
  > docker login
  > docker image push smalltides/alpine (push to dockerhub)
  > docker image tag smalltides/alpine smalltides/alpine:testing
  > docker image ls
  > docker image push smalltides/alpine:testing
```
Building Images: The Dockerfile
```
  > docker build -t <new image name> .
  > docker build -t <new image name> -f <Dockerfile Name> 
  > FROM, ENV, RUN, EXPOSE, COPY, CMD (some Dockfile command)
```
Building Images: Extending Official Nginx Images
```
  > docker container run -p 80:80 --rm nginx
  > curl 127.0.0.1
  > cd dockerfile-sample-2
  > docker build -t nginx-with-html .
  > docker container run -p 80:80 --rm nginx-with-html
  > curl 127.0.0.1 (watch the response html)
  > docker image tag nginx-with-html smalltides/nginx-with-html:latest
  > docker image push smalltides/nginx-with-html:latest
```
Build Your Own Dockerfile and Run Containers From It
```
  > cd dockerfile-assignment-1
  > docker build -t testnode .
  > docker container run --rm -p 80:3000 testnode
  > curl 127.0.0.1 (see Node.js Express App on page)
  > docker image tag testnode smalltides/testnode
  > docker image push smalltides/testnode
  > docker image rm smalltides/testnode
  > docker container run --rm -p 80:3000 smalltides/testnode (download from docker hub)
  > curl 127.0.0.1 (see Node.js Express App on page)
  > https://github.com/BretFisher/node-docker-good-defaults (docker node dev template)
```
Container Lifetime & Persistent Data
```
  > https://12factor.net/zh_cn/
  > https://medium.com/@kelseyhightower/12-fractured-apps-1080c73d481c
```
Persistent Data: Data Volumes
```
  > docker pull mysql
  > docker image inspect mysql
  > docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True mysql
  > docker container inspect mysql (see volume)
  > docker volume list
  > docker volume inspect <volume_id>
  > docker container run -d --name mysql2 -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql (named volume)
  > docker volume list (see a volume named mysql-db)
  > docker container inspect mysql2
  > docker volume inspect mysql-db
  > docker container run -d --name mysql3 -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql (container mysql3 use mysql-db volume)
  > docker volume create --help
```
Persistent Data: Bind host Mounting in container
```
  > cd dockerfile-sample-2
  > docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx (mount host file in container)
  > docker container inspect nginx
```
Database Upgrades with Named Volumes
```
  > docker container run -d --name postgres -v psql-data:/var/lib/postgresql/data postgres:9.6.1 (named volume)
  > docker volume list (see psql-data volume)
  > docker volume inspect psql-data
  > docker container inspect postgres
  > docker container logs postgres
  > docker container stop postgres
  > docker container rm postgres
  > docker container run -d --name postgres -v psql-data:/var/lib/postgresql/data postgres:9.6.2
  > docker volume list (see psql-data volume)
  > docker container logs postgres
```
Edit Code Running In Containers With Bind Mounts
```
  > https://jekyllrb.com
  > cd bindmount-sample-1
  > docker container run -p 80:4000 -v $(pwd):/site bretfisher/jekyll-serve ( $(pwd) for get current folder to binding into container) 
  > curl 127.0.0.1 (if edit the code of bindmount-sample-1, will see the instant change)
```
Docker Compose: The Multi-Container Tool
```
  > https://docs.docker.com/compose/compose-file/compose-versioning
  > https://github.com/docker/compose/releases
  > curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose chmod +x /usr/local/bin/docker-compose (install on Linux)
```
Basic Compose Commands
```
  > cd compose-sample-2
  > docker-compose up
  > curl 127.0.0.1 (nginx 80 port in and then proxy to httpd 80 port)
  > docker-compose logs
  > docker-compose ps
  > docker-compose top
  > docker-compose down
```
Build a Compose File For a Multi-Container Service, drupal and postgres
```
  > cd compose-assignment-1
  > docker-compose up
  > docker volume ls
  > docker-compose down (down and not remove volume)
  > docker-compose down -v (down and remove volume)
```
Adding Image Building to Compose Files
```
  > https://docs.docker.com/compose/compose-file/#build
  > cd compose-sample-3
  > docker-compose up
  > docker volume ls
  > docker-compose ps
  > docker-compose top
  > docker-compose down (down and not remove volume)
  > docker-compose down -v (down and remove volume)
```
Compose For Run-Time Image Building and Multi-Container Dev and Testing
```
  > cd compose-assignment-2
  > docker-compose up
  > docker volume ls
  > docker volume inspect composeassignment2_drupal-data
  > docker-compose ps
  > docker-compose top
  > docker-compose down (down and not remove volume)
  > docker-compose up (because don't delete volume, some the previous data is keep)
  > docker-compose down -v (down and remove volume)
```
Swarm Mode: Built-In Orchestration
```
  > https://www.youtube.com/watch?v=dooPhkXT9yI
  > https://www.youtube.com/watch?v=_F6PSP-qhdA
  > https://speakerdeck.com/aluzzardi/heart-of-the-swarmkit-topology-management
  > https://www.youtube.com/watch?v=EmePhjGnCXY
  > http://thesecretlivesofdata.com/raft/
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/swarm-cluster.png "swarm-cluster")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/manager-worker.png "manager-worker")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-service.png "docker-service")

Create Your First Service and Scale It Locally, one node, one service, multiple container
```
  > https://docs.docker.com/engine/swarm/services
  > docker info (see Swarm active or inactive)
  > docker swarm init (enable swarm)
  > docker info (see Swarm: active now)
  > docker swarm join --token SWMTKN-1-0xc30pitylk8o4mbr2n0zvp8p0j53ypm904pmrwo1hx9xpmkz1-2cr1m9luu02t3tm9ri0cvy2oa 192.168.65.2:2377 (node join cluster command)
  > docker node ls (see a manager node)
  > docker swarm --help
  > docker service --help
  > docker service create alpine ping 8.8.8.8
  > docker image ls
  > docker container ls
  > docker service ls
  > docker service ps <service id>
  > docker service update <service id> --replicas 3
  > docker container ls (see 3 container)
  > docker service ls (see replicas 3/3)
  > docker service ps <service id> (see 3 container run on 1 node)
  > docker update --help
  > docker service update --help
  > docker container rm -f <container id> (force delete a container)
  > docker service ls (see replicas 2/3, but later become 3/3)
  > docker service ps <service id> (see some Running and Shutdown container)
  > docker service rm <service id>
  > docker container ls (see 0 container)
```
Creating a 3-Node Swarm Cluster, on digitalocean
```
  > https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets
  > https://www.bretfisher.com/docker-swarm-firewall-ports/
  > https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client
  > http://get.docker.com
  >
  > create 3 node on digitalocean and setting ssh key
  > ssh root@<digitalocean machine ip> (for 3 nodes)
  > curl -sSL https://get.docker.com | sh  (for 3 nodes)
  > sudo usermod -aG docker root  (for 3 nodes)
  > docker swarm init --advertise-addr <digitalocean node1 ip> (on node1)
  > docker swarm join --token SWMTKN-1-1qgl3tya7k1206d4ph4hsf04f708dnem181rxfv40k08yvd5bd-64uuisxvtm0ts90zpv3jgc5gx <digitalocean node1 ip>:2377 (on node2)
  > docker swarm join --token SWMTKN-1-1qgl3tya7k1206d4ph4hsf04f708dnem181rxfv40k08yvd5bd-64uuisxvtm0ts90zpv3jgc5gx <digitalocean node1 ip>:2377 (on node2)
  > docker node ls (on node1, cluster see 3 nodes, 1 for manager 2 for worker)
  > docker node update --role manager node2 (on node1, change node2 to manager role)
  > docker swarm leave (on node3)
  > docker swarm join-token manager (on node1)
  > docker swarm join --token SWMTKN-1-1qgl3tya7k1206d4ph4hsf04f708dnem181rxfv40k08yvd5bd-a6khjsun9lkadou2i9w7jz54x <digitalocean node1 ip>:2377 (on node3, join swarm cluster to be a manager node)
  > docker service create --replicas 3 alpine ping 8.8.8.8 (on node1)
  > docker service ls (on node1)
  > docker service ps <service id> (see app run on node1,2,3 status)
  > docker node ps <node id> (see app run on node status)
  > docker container ls (on node1, container name = service_name.num.node_app_id, gracious_brown.3.q9mku3dfkwu6fby4i57du92w2)
  > service see swarm cluster (contain some nodes), deploy app to run on nodes, use docker node ps <node id> to see apps on node, docker container ls to see real container on node
```
Scaling Out with Overlay Networking (on digitalocean)
```
  > docker network ls (default ingress network for swarm)
  > docker network create --driver overlay mydrupal (on node1, but node2 and node3 sync create mydrupal network)
  > docker network inspect mydrupal
  > docker service create --name psql --network mydrupal -e POSTGRES_PASSWORD=mypass postgres (on node1)
  > docker service ls
  > docker service ps psql (on node1, see the app detail in psql service)
  > docker container logs psql.1.onomutb8sixz8xrg1od4k298g
  > docker service create --name drupal --network mydrupal -p 80:80 drupal (on node1)
  > docker service ls
  > docker service ps psql (see psql run on node1)
  > docker service ps drupal (see drupal run on node2)
  > docker node ps node1, docker node ps node2
  > watch docker service ls (monitor docker service status)
  > http://<node2_ip> (see drupal site)
  > docker service inspect drupal
  > docker service inspect psql
```
Scaling Out with Routing Mesh (on digitalocean)
```
  > https://docs.docker.com/engine/swarm/ingress
  > docker service create --name search --replicas 3 -p 9200:9200 elasticsearch:2 (on node1)
  > docker service ls
  > docker service ps <service id> (see a docker service run on different node)
  > docker service ps search
  > docker node ps <node id> (see a node run different node)
  > docker node ps node1
  > curl 127.0.0.1:9200 (on node1, but swarm cluster load balance the request for tree node elasticsearch instance)
  > swarm cluster load balance is stateless
  > swarm cluster load balance on Layer3(TCP), not Layer4(DNS)
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/swarm-lb.png "swarm-lb")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/swarm-routing1.png "swarm-routing1")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/swarm-routing2.png "swarm-routing2")

 Create A Multi-Service Multi-Node Web Vote App (on digitalocean)
 ```
   > https://docs.docker.com/engine/swarm/services/
   > python voting app -> redis queue -> .NET worker -> postgres DB -> node.js show result 
   > docker network create -d overlay backend (on node1)
   > docker network create -d overlay frontend (on node1)
   > docker network ls (see node1,2,3 sync create network)
   > docker service create --name vote -p 80:80 --network frontend --replicas 2 dockersamples/examplevotingapp_vote:before (on node1)
   > docker service create --name redis --network frontend redis:3.2 (on node1)
   > docker service create --name worker --network frontend --network backend dockersamples/examplevotingapp_worker
   > docker service create --name db --network backend --mount type=volume,source=db-data,target=/var/lib/postgresql/data postgres:9.4
   > docker service create --name result --network backend -p 5001:80 dockersamples/examplevotingapp_result:before
   > docker service ls
   > docker service ps result
   > docker service ps vote
   > docker service ps worker
   > docker service ps db
   > docker service ps redis
   > http://<node_ip>
   > http://<node_ip>:5001
 ```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/swarm-app-1-architecture.png "swarm-app-1-architecture")

Swarm Stacks and Production Grade Compose (on digitalocean)
```
  > docker stack deploy (in stack mode, compose file can't build,because this for production)
  > cd swarm-stack-1
  > docker stack deploy -c example-voting-app-stack.yml voteapp (on digitalocean node1)
  > docker service ls
  > docker stack ls
  > docker stack services voteapp
  > docker stack ps voteapp
  > docker network ls
  > docker volume ls
  > change example-voting-app-stack.yml vote:deploy:replicas from 2 to 5
  > docker stack deploy -c example-voting-app-stack.yml voteapp (on node1, see vote app become 5 instances)
  > docker stack rm voteapp
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-stack1.png "docker-stack1")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-stack2.png "docker-stack2")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/node-instance.png "node-instance")

Secrets Storage for Swarm: Protecting Your Environment Variables, Using Secrets in Swarm Services (on digitalocean)
```
  > https://docs.docker.com/engine/swarm/secrets/
  > cd secrets-sample-1
  > docker secret create psql_user psql_user.txt (on node1)
  > docker secret inspect psql_user psql_user
  > docker secret ls
  > echo "myDBpassWORD" | docker secret create psql_pass -
  > docker service create --name psql --secret psql_user --secret psql_pass -e POSTGRES_PASSWORD_FILE=/run/secrets/psql_pass -e POSTGRES_USER_FILE=run/secrets/psql_user postgres
  > docker service ls
  > docker node ps
  > docker service ps psql
  > docker exec -it psql.1.ty99wnavjmm9b9gmg1j06iy9n bash
  > ls /run/secrets/
  > cat /run/secrets/psql_pass
  > cat /run/secrets/psql_user
  > exit
  > docker container logs psql.1.ty99wnavjmm9b9gmg1j06iy9n  
  > docker service update --secret-rm psql_pass psql (this command will redeploy the service, but postgres can't up, because no password) 
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-secret1.png "docker-secret1")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-secret2.png "docker-secret2")

Using Secrets with Swarm Stacks (on digitalocean)
```
  > https://docs.docker.com/compose/compose-file/#secrets-configuration-reference
  > cd secrets-sample-2 (on node1)
  > docker stack deploy -c docker-compose.yml mydb
  > docker service ls
  > docker secret ls
  > docker stack rm mydb
  > docker secret ls
```
Using Secrets With Local Docker Compose (on local)
```
  > cd secrets-sample-2 (on local machine)
  > docker-compose up -d
  > docker-compose exec psql cat /run/secrets/psql_user
  > docker secret ls (compose use fake local secret, so see no secrets)
```
Create A Stack with Secrets and Deploy (on digitalocean)
```
  > cd swarm-stack-2
  > echo "<your_pw>" | docker secret create psql-pw -
  > docker stack deploy -c stack-with-build-deploy-secret.yml drupal (on node1)
  > docker stack ps drupal
  > http://<node_ip>:8080
  > ocker stack rm drupal
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/stack-secret.png "stack-secret")

Full App Lifecycle: Dev, Build and Deploy With a Single Compose Design
```
  > https://docs.docker.com/compose/extends/#multiple-compose-files
  > https://docs.docker.com/compose/production/
  >
  > cd swarm-stack-3
  > docker-compose.yml (the common config of all compose file)
  > docker-compose.override.yml (for local development, docker-compose up)
  > docker-compose.test.yml (for test, for CI)
  > docker-compose.prod.yml (for production, for CD)
  >
  > docker-compose up -d (default select docker-compose.override.yml, dev)
  > http://127.0.0.1:8080
  > docker container exec -it swarmstack3_drupal_1 bash
  > exit
  > docker-compose down
  >
  > docker-compose -f docker-compose.yml -f docker-compose.test.yml up -d (testing CI)
  > docker-compose down
  >
  > docker-compose -f docker-compose.yml -f docker-compose.prod.yml config
  > docker-compose -f docker-compose.yml -f docker-compose.prod.yml config > output.yml (production CD)
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-cicd.png "docker-cicd")

Service Updates: Changing Things In Flight
```
  > docker service update --image myapp:1.2.1 <service name>
  > docker service update --env-add NODE_ENV=production --publish-rm 8080
  > docker service scale web=8 api=6
  > docker stack deploy -c file.yml <stack name>
  >
  > docker service create -p 8080:80 --name web nginx:1.13.7
  > docker service ls
  > docker service scale web=5
  > docker service update --image nginx:1.13.6 web
  > docker service update --publish-rm 8080 --publish-add 9090:80 web
  > docker service update --force web
  > docker service rm web
```
Healthchecks in Dockerfiles
```
  > docker container run --name p1 -d postgres
  > docker container ls
  > docker container run --name p2 -d --health-cmd="pg_isready -U postgres || exit 1" postgres
  > docker container inspect p2
  > docker service create --name p1 postgres
  > docker service create --name p2 --health-cmd="pg_isready -U postgres || exit 1" postgres
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health1.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health2.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health3.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health4.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health5.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health6.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health7.png "docker-health")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/health8.png "docker-health")

Docker Hub, Store and Cloud
```
  > https://hub.docker.com
  > https://store.docker.com
  > https://cloud.docker.com
  > https://www.youtube.com/watch?v=VJmbCioYKGg (Docker Cloud Fleet Management and Collaboration)
```
Understanding Docker Registry
```
  > https://docs.docker.com/registry/configuration/
  > https://docs.docker.com/registry/garbage-collection/
  > https://docs.docker.com/registry/recipes/mirror/
```
Run a Private Docker Registry
```
  > https://github.com/docker/distribution
  > cd registry-sample-1
  > docker container run -d -p 5000:5000 --name registry registry
  > docker container ls
  > docker image ls
  > 
  > docker pull hello-world
  > docker run hello-world
  > docker tag hello-world 127.0.0.1:5000/hello-world (push to local registry)
  > docker image ls
  > docker push 127.0.0.1:5000/hello-world (push to local registry)
  > docker image rm hello-world
  > docker image rm 127.0.0.1:5000/hello-world
  > docker image ls
  > docker pull 127.0.0.1:5000/hello-world:latest
  > docker image ls
  > docker container kill registry
  > docker container rm registry
  > docker container run -d -p 5000:5000 --name registry -v $(pwd)/registry-data:/var/lib/registry registry
  > docker push 127.0.0.1:5000/hello-world (push to local registry, see the local registry-data folder)
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-registry1.png "docker-registry1")
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/docker-registry2.png "docker-registry2")

Secure Docker Registry With TLS and Authentication
```
  > http://training.play-with-docker.com/linux-registry-part1
  > http://training.play-with-docker.com/linux-registry-part2
```
Using Docker Registry With Swarm (on play-with-docker.com)
```
  > http://labs.play-with-docker.com
  > create a 5 managers swarm cluster
  > docker node ls (on node1)
  > docker service create --name registry -p 5000:5000 registry (on node1)
  > docker service ps registry (on node1)
  > see http://pwd10-0-29-3-5000.host1.labs.play-with-docker.com/v2/_catalog (node1 url)
  > see http://pwd10-0-29-6-5000.host1.labs.play-with-docker.com/v2/_catalog (node2 url)
  > docker pull hello-world (on node1)
  > docker image ls (on node1)
  > docker image ls (on node2)
  > docker tag hello-world 127.0.0.1:5000/hello-world (on node1)
  > docker push 127.0.0.1:5000/hello-world (on node1)
  > see http://pwd10-0-29-3-5000.host1.labs.play-with-docker.com/v2/_catalog (node1 url)
  > docker pull nginx (on node1)
  > docker tag nginx 127.0.0.1:5000/nginx (on node1)
  > docker push 127.0.0.1:5000/nginx (on node1)
  > docker image ls (on node1)
  > see http://pwd10-0-29-3-5000.host1.labs.play-with-docker.com/v2/_catalog (node1 url)
  > docker service create --name nginx -p 80:80 --replicas 5 --detach=false 127.0.0.1:5000/nginx (on node1)
  > docker service ps nginx (see 5 nginx replicas run on 5 node)
```
![alt text](https://github.com/smalltide/docker-mastery/blob/master/img/registry-swarm.png "registry-swarm")

Third Party Image Registries
```
  > https://quay.io
  > https://quay.io/plans/?tab=enterprise
  > https://about.gitlab.com/2016/05/23/gitlab-container-registry
```