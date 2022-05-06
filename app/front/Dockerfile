FROM node:16-alpine AS build-env

RUN apk upgrade && apk update

WORKDIR /app/
COPY ./package.json /app/
RUN npm --unsafe-perm install
RUN npm ci
COPY . /app/

EXPOSE 4200

ENTRYPOINT [ "npm" ]
CMD [ "start" ]