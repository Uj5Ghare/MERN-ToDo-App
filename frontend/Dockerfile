ARG VERSION=lts-alpine
ARG DIR=/home/react/

FROM node:$VERSION AS Build

WORKDIR $DIR

COPY package.json $DIR

RUN npm install


FROM node:$VERSION

WORKDIR $DIR

#To connect backend container,both container networks must be same & set backend container name as backend 
ENV BACKEND_CONTAINER_NAME=backend   

ENV BACKEND_NETWORK=mern-net

COPY --from=Build $DIR/node_modules $DIR/node_modules

COPY . $DIR

EXPOSE 3000

ENTRYPOINT ["npm"]

CMD ["start"]
