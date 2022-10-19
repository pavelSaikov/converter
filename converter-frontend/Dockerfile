FROM node:16-slim AS build

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

FROM nginx:alpine

COPY .nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/converter-frontend /usr/share/nginx/html
