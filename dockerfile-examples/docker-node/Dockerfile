FROM node
MAINTAINER Ouadie LAHDIOUI
# Create app directory
RUN mkdir -p /app
WORKDIR /app

# Install app dependencies
# COPY package.json /app


# Bundle app source
COPY . /app
RUN npm install

EXPOSE 8080
CMD [ "npm", "start" ]