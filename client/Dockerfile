FROM node:alpine as builder
WORKDIR '/app'
COPY ./pakage.json ./
RUN npm install
COPY . .
RUN npm run builder

FROM ngnix
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
