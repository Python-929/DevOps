### DevOps Bootcamp Capstone Project ###
### Sumi Jung  #########################
### April 17th, 2023 ###################

# To create a Node.js application, 
FROM node:16.13.1

# Define the working directory of a Docker container
WORKDIR /home/ansible_controller

# Copy package*.json & package-lock.json files to the container
COPY package*.json ./

# Copy ./public and ./src of the project hello-world to the container
COPY ./public ./public
COPY ./src ./src

# Install the node.js dependencies
RUN npm install

# Set a UserID and Password
#RUN useradd -rm -d /home/ansible_controller -s /bin/bash -g root -G sudo -u 1001 ansible_controller
#RUN echo ansible_controller:12345 | chpaswd

# No Password Required
#RUN echo "ansible_controller ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

# Expose: Define the network ports that this container will listen on at runtime
EXPOSE 3000

# Run SSH script -> start the hello-world application
CMD ["npm","start"]