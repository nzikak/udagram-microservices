## Build
FROM node:14-alpine AS node
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
# Bundle app source
RUN npm install -g @ionic/cli
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=node  /usr/src/app/www /usr/share/nginx/html