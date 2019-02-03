# This setup uses multi stage build for copying build files
# pkg docs: https://github.com/zeit/pkg

# In the builder stage
# pkg bundles of source code and node environment to make a executable binary
# At line 18, index is the binary name of our source code
# If you want to change the name of the binary
# Make sure you also change all the reference of the binary name i.e. line 26 and line 27


# Builder Stage =======
FROM node:lts-alpine AS builder
RUN mkdir -p /usr/src/build 
WORKDIR /usr/src/build
COPY package*.json ./
RUN npm i --production && npm i -g pkg
COPY . .
RUN pkg -t alpine-x64 -o index .

# Deploy Stage =======
FROM alpine:latest
RUN apk update && apk add --no-cache libstdc++ libgcc
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
EXPOSE 5000
COPY --from=builder /usr/src/build/index /usr/src/app
CMD [ "./index" ]