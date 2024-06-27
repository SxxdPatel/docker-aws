# Stage 1: Build the React app
FROM node:16-alpine AS build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serve the React app with Nginx
FROM nginx

COPY --from=build /app/build /usr/share/nginx/html

COPY ./ngnix/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000
