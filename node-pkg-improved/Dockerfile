# Note:
# You have to add build script in the package.json to build this project with pkg
# Also refer to ./package.json
# 
# "script": {
#       "build": "pkg -t alpine-x64 -o binary ."
# }
# 

# Before building docker image
# please run: npm run build
# to build binary

FROM alpine:latest
RUN apk update && apk add --no-cache libstdc++ libgcc
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
EXPOSE 5000
COPY ./binary /usr/src/app
CMD [ "./binary" ]