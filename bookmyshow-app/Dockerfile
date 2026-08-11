FROM node:18 AS builder
ENV NODE_OPTIONS=--openssl-legacy-provider
WORKDIR /App
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:latest
COPY --from=builder /App/build /usr/share/nginx/html
EXPOSE 80
