FROM node:alpine as builder

RUN apk update && \
    apk add python make g++ && \
    rm -rf /var/cache/apk/*

COPY package*.json ./

RUN npm install --only=production
RUN npm prune --production

FROM node:alpine

RUN mkdir -p /app/node

RUN chown -R node:node /app

WORKDIR /app/node

COPY --from=builder node_modules node_modules

COPY . .

USER node

EXPOSE 3000

CMD [ "npm", "run", "start" ]
