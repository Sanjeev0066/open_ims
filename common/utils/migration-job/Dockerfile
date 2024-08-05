FROM node:22.5.1-alpine3.19

WORKDIR /home/node/app

COPY ./package.json ./
# USER root
RUN npm install
COPY ./ ./
# USER node

# CMD ["npm", "run", "migrate"]