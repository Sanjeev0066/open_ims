FROM node:22.5.1-alpine3.19 as builder

WORKDIR /home/node/app

COPY ./package.json ./
RUN npm install
COPY ./ ./

RUN npm run build
RUN chown -R node:node /home/node/app/dist


FROM node:22.5.1-alpine3.19

WORKDIR /home/node/app

EXPOSE 3000

COPY ./package.json ./
RUN npm install --omit=dev
RUN chown -R node:node /home/node/app

COPY --from=builder /home/node/app/dist ./dist

CMD ["npm", "run", "start"]