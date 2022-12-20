# empty-vue-ts

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Run your end-to-end tests
```
npm run test:e2e
```

### Lints and fixes files
```
npm run lint
```

### DockerFile
```
# build stage
FROM node:lts-alpine as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```


### Build container
```
docker build -t docker-vuets-nginx .
```

### Run container
```
docker run -it -p 8080:80 -d --name vuets-nginx docker-vuets-nginx
```

### Stop container
```
docker stop vuets-nginx
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
