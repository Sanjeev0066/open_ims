FROM node:22.5.1-alpine3.19 as builder

WORKDIR /home/node/app

COPY ./package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

# Slimmed production image
FROM nginx:1.24.0

EXPOSE 5000

COPY --from=builder /home/node/app/dist /usr/share/nginx/html
COPY /nginx/default.conf /etc/nginx/conf.d/default.conf