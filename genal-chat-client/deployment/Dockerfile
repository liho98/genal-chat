FROM node:10.16.3 as build-stage

WORKDIR /client-app
COPY genal-chat-client /client-app
RUN npm ci
RUN npm run build

FROM nginx
COPY  --from=build-stage /client-app/dist /usr/share/nginx/html
COPY --from=build-stage /client-app/deployment/nginx.conf /temp/nginx.conf
RUN envsubst /client-app < /temp/nginx.conf > /etc/nginx/conf.d/default.conf
EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"] 