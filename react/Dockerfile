# This setup uses multi stage build for copying build files
# In the builder stage
# We are building our react project
# Which gives us static build files which we can deploy
# For the Deploy stage
# We copied our build file and making a nginx server
# Which we use to serve our static build files
# We also added some configuration to nginx server to server the files

# Builder Stage =======
FROM node:lts-alpine AS builder
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm i
COPY . .
ENV NODE_ENV=production
ENV GENERATE_SOURCEMAP=false
RUN npm run build

# Deploy Stage =======
FROM nginx:alpine
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/src/app/build /usr/share/nginx/html