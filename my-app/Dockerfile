### STAGE 1: Build ###
FROM node:lts-alpine AS build

WORKDIR /dist/src/app

RUN npm cache clean --force

COPY . .
RUN npm install
RUN npm run build --prod


FROM nginx:latest AS ngi

COPY --from=build /dist/src/app/dist/my-app /usr/share/nginx/html
COPY /nginx.conf  /etc/nginx/conf.d/default.conf
# Exposing a port, here it means that inside the container
# the app will be using Port 80 while running
EXPOSE 80
