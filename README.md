## docker-compose v2 format 

Use with docker-compose v1.8 or later only to create stack for swarm mode docker 1.12 or later.

#### customize the deployment

edit `docker-compose.override.yml` to set the URL hostname


#### build the DAB file

`BRANCH=develop INPORT=3020 docker-compose bundle`

You can change the INPORT above. You can change the BRANCH between `latest` and `develop`.

Note that there will be warning about network key. That is expected.

#### deploy the stack on your swarm

`docker deploy rocketchatdev`

Note that the project (stack) name may be different in your case.

This will start the entire stack - mongo, rockechat, and the overlay network.

#### make the stack available from the hosts

Since host port is non-portable, it is not included in docker-compose build.  

Add it to service after deployment:

`docker service update -p 3020:3020 rocketchatdev_rocketchat`

Again your project (stack) name may be different.


