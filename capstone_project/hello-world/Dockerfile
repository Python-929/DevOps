### DevOps Bootcamp Capstone Project ###
### Sumi Jung  #########################
### April 17th, 2023 ###################

# To create a Node.js application, 
FROM node:16.13.1

#Install ssh
RUN apt-get update  -y \
    && apt-get upgrade -y \ 
    && apt-get install -y \
    ssh \
    sshpass \
    sudo \
    software-properties-common

# Set a UserID and Password
RUN useradd -rm -d /home/sumi -s /bin/bash -g root -G sudo -u 1001 sumi
RUN echo sumi:103 | chpasswd

# No Password Required
RUN echo "sumi ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

WORKDIR /home/sumi

#COPY startup.sh ./
COPY startup.sh ./

# Copy package*.json & package-lock.json files to the container
COPY package*.json ./

# Copy ./public and ./src of the project hello-world to the container
COPY ./public ./public
COPY ./src ./src

# Install the node.js dependencies
RUN npm install

# make .ssh directory
RUN mkdir -p /home/sumi/.ssh

# Expose: Define the network ports that this container will listen on at runtime
EXPOSE 3000

EXPOSE 22

# Run SSC script -> start the hello-world application
# CMD ["/bin/bash", "/home/ansible_controller/startup.sh"]
CMD ["/bin/bash", "/home/sumi/startup.sh"]