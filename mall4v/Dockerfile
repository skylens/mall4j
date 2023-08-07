FROM node:16-bookworm-slim AS build
COPY . /app
WORKDIR /app
RUN npm install --registry=https://registry.npmmirror.com && npm run build

FROM nginx:1.25-bookworm
ENV TimeZone=Asia/Shanghai
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]