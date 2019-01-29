# Using smallest and stable node image
FROM node:lts-alpine

# Creating current working directory
RUN mkdir -p /usr/src/app

# Setting default working directory
# Important for executing commands later
WORKDIR /usr/src/app

# Copying package and package lock 
# For installing dependencies in the image
COPY package*.json ./

# Installing only dependencies
# Not devDependency as they required only for development
RUN npm i --production

# Copying our code
COPY . .

# Setting default command for the image
# This command will be triggered by the container
# To boot up the image inside the container
CMD [ "npm", "start" ]