FROM node:alpine as builder

RUN apk update && \
    apk add python make g++ && \
    rm -rf /var/cache/apk/*

RUN mkdir -p /app/express
RUN chown -R node:node /app
WORKDIR /app/express
COPY ./package.json .

# Production Environment
FROM builder as production
ENV NODE_ENV=production
RUN npm install --only=production
RUN npm prune --production
COPY . .
CMD ["node", "bin/www"]

# Development Environment
FROM builder as dev
ENV NODE_ENV=development
RUN npm install -g nodemon && npm install
COPY . .
CMD ["nodemon", "bin/www"]
