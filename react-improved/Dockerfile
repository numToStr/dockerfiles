# Before building docker image
# please run: npm run build
# to build your react app locally and 
# then send the build files to docker daemon to build the docker image

FROM nginx:alpine
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY ./build /usr/share/nginx/html