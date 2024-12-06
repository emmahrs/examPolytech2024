FROM node:10-alpine as builder
LABEL maintainer="emma"
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:1.27-alpine
COPY nginx/ /etc/nginx
COPY --from=builder /app/dist/ /usr/share/nginx/html
COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh
RUN chmod +x /docker-entrypoint.d/entrypoint.sh
