FROM node:20
WORKDIR /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
# for bridge network
ENV DB_HOST="mysql"
# For host network
#ENV DB_HOST="localhost"
CMD ["node", "index.js"]


# set DB_HOST="msql container name" because the container IP changes if container is restarted

# docker build -t backend:1.0.0 .
# docker run -d --name backend backend:1.0.0

# docker logs backend

# backend app cannot connect to mysql DB because of docker default network 

# if you are using default n/w docker containers can't communicate with each other

# For containers to communicate we need to create network

# docker network create expense
# docker network ls

# disconnect the containers from default network and add them to the network created

# docker network disconnect <NetworkName> <ContainerName>
# docker network connect <NetworkName> <ContainerName>

# docker network disconnect bridge mysql
# docker network connect expense mysql

# docker rm backend

# run the container with expense network
# docker run -d --name backend --network expense backend:1.0.0  
# docker inspect backend

# docker exec -it backend bash
# telnet mysql 3306


################# For host network #################
# docker build -t backend:1.0.0 .
# docker run -d --name backend --network host backend:1.0.0