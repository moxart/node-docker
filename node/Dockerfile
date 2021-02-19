FROM node:latest

ENV NODEMON=/home/app/node/node

RUN mkdir -p /app/node

WORKDIR /app/node

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "npm", "run", "start:dev" ]
