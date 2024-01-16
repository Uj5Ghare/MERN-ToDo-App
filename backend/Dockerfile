ARG VERSION=lts-alpine
ARG DIR=/home/node/

FROM node:$VERSION AS Build

WORKDIR $DIR

COPY package.json $DIR

RUN npm install


FROM node:$VERSION

WORKDIR $DIR

#To connect mongo container,both container networks must be same & set db container name as mongo
ENV DB_COTAINER_NAME=mongo

ENV DB_NETWORK=mern-net

COPY --from=Build $DIR/node_modules $DIR/node_modules

COPY . $DIR

EXPOSE 5000

ENTRYPOINT ["node"]

CMD ["index.js"]
