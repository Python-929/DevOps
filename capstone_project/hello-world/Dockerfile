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

# Define the working directory of a Docker container
WORKDIR /home/sumi

#COPY startup.sh ./
COPY startup.sh .

# Copy package*.json & package-lock.json files to the container
COPY package*.json ./


# Copy ./public and ./src of the project hello-world to the container
COPY ./public ./public
COPY ./src ./src

# Install the node.js dependencies
RUN npm install

# Set a UserID and Password
RUN useradd -rm -d /home/sumi -s /bin/bash -g root -G sudo -u 1001 sumi
RUN echo sumi:103 | chpasswd

# No Password Required
RUN echo "sumi ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

# create .ssh dir
RUN mkdir -p /home/sumi/.ssh

# Expose: Define the network ports that this container will listen on at runtime
EXPOSE 3000

# Run SSH script -> start the hello-world application
#CMD ["npm","start"]
CMD ["/bin/bash", "/home/sumi/startup.sh"]