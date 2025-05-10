#FROM node:20
FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json ./
COPY *.js ./
RUN npm install


FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
ENV DB_HOST="mysql"
WORKDIR /opt/backend
USER expense
COPY --from=builder /opt/backend /opt/backend
CMD ["node", "index.js"]


# Create infra using 27-terraform-aws-eks repo
# 27-terraform-aws-eks
# ---------------------
# 00-vpc
# 10-sg
# 20-bastion
# 40-eks
# 30-rds

# Create 3 images from Bastion to test blue-green deployment after creating eks infra using terraform
# ---------------------------------------------------------------------------------------------------
# 29-expense-docker repo same as 18-expense-docker ---> cd 02 backend

# In 29-expense-docker repo

# For blue
# change     res.json("This is the health check for blue 1.0.0");
# commit and push to git

# In Bastion
# git clone https://29-expense-docker

# cd expense-docker
# cd backend

# docker build -t dath1/backendbluegreen:1.0.0 .
# docker login -u dath1
# docker push dath1/backendbluegreen:1.0.0

# In 29-expense-docker repo
# For green
# change      res.json("This is the health check for green 2.0.0");
# commit and push to git

# In Bastion
# git pull
# docker build -t dath1/backendbluegreen:2.0.0 .
# docker login -u dath1
# docker push dath1/backendbluegreen:2.0.0

# In 29-expense-docker repo
# For blue
# change      res.json("This is the health check for blue 3.0.0");
# commit and push to git

# In Bastion
# git pull
# docker build -t dath1/backendbluegreen:3.0.0 .
# docker login -u dath1
# docker push dath1/backendbluegreen:3.0.0