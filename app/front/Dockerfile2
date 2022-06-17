FROM node:16-alpine AS build

WORKDIR /app
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build:prod

FROM nginx:1.21-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/front /usr/share/nginx/html