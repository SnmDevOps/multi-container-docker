FROM node:14.14.0-alpine as builder

MAINTAINER snmmaurya

WORKDIR '/app'

COPY package.json .

RUN npm install

COPY . .

RUN npm run build




FROM nginx as runner

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html