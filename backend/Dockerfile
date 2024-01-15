ARG VERSION=lts-alpine
ARG DIR=/home/node/

FROM node:$VERSION AS Build

WORKDIR $DIR

COPY package.json $DIR

RUN npm install


FROM node:$VERSION

WORKDIR $DIR

COPY --from=Build $DIR/node_modules $DIR/node_modules

COPY . $DIR

EXPOSE 5000

ENTRYPOINT ["node"]

CMD ["index.js"]
