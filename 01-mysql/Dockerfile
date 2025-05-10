FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1
COPY scripts/*.sql /docker-entrypoint-initdb.d

# docker build -t mysql:1.0.0 .
# docker run -d --name mysql mysql:1.0.0

# docker exec -it mysql bash
# mysql -u root -pExpenseApp@1
# show databases;
# use transactions;
# show tables;

# ifconfig
# docker inspect mysql  # to get container IP


# For containers to communicate we need to create network

# docker network create expense
# docker network ls

# disconnect the containers from default network and add them to the network created

# docker network disconnect <NetworkName> <ContainerName>
# docker network connect <NetworkName> <ContainerName>

# docker network disconnect bridge mysql
# docker network connect expense mysql

############ For host network ##################
# docker build -t mysql:1.0.0 .
# docker run -d --name mysql --network host mysql:1.0.0

# For each modem there is Ip address and ISP provides external IP and
# the modem will assign a Ip address for each device connected to it

# ifconfig

# Similarly at the time of docker installation docker creates its own network and 
# docker creates virtual modem and it has Ip address 
# and it will assgin a Ip for each container

# if you are using default n/w docker containers can't communicate with each other

# For containers to communicate we need to create network 

# In Host network container will use host ip and ports
# Bridge network will create virtual bridge network and containers will be attached to bridge network 
# we can communicate between containers

# For host network use localhost instead of container name(dns)

# Host network is less secure and ports will exhaust
