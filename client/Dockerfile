FROM node:lts-alpine as builder

WORKDIR '/client'

COPY ./package.json ./

RUN npm install

COPY ./ ./

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /client/build /usr/share/nginx/html