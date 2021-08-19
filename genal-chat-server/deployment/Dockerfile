FROM node:10.16.3 as build-stage

WORKDIR /server-app
COPY genal-chat-server /server-app
RUN npm i pm2 -g
RUN npm i
RUN npm run build

CMD ["npm", "run", "pm2"] 