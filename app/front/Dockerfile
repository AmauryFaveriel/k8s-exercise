#################
# Build the app #
#################
FROM node:16-alpine as build
WORKDIR /app
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build:prod

################
# Run in NGINX #
################
FROM nginx:1.21-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/front /usr/share/nginx/html

# When the container starts, replace the env.js with values from environment variables
CMD ["/bin/sh",  "-c",  "envsubst < /usr/share/nginx/html/assets/env.template.js > /usr/share/nginx/html/assets/env.js && exec nginx -g 'daemon off;'"]
