# Stage 1: Build Angular App
FROM node:18 AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# Stage 2: Serve with Nginx
FROM nginx:latest
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80