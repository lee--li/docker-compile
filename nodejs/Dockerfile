FROM node:12-alpine as base

FROM base as builder

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install --only=production

FROM base

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/node_modules ./node_modules

COPY . .

EXPOSE 8080

#ENV PORT 8081

ENTRYPOINT [ "node", "servernode.js" ]
