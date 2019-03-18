
#
#Build base container from node:alpine base image as set name as builder
#
FROM node:alpine as builder
WORKDIR /app

#copy package.json to work directroy and intall dependencies
COPY ./package*.json ./
RUN npm install 

#copy all files from local dev to container
COPY . .

#run build to build react app production and file build will store at /app/build
RUN npm run build

#
#install nginx from base image 
#
FROM nginx

#copy and repalce customize default.conf configuration file
COPY ./ngix/default.conf /etc/nginx/conf.d/default.conf

#copy build files to nginx public folder
COPY ./app/build ./usr/share/nginx/html

