FROM node:16-alpine as builder

WORKDIR /app
COPY ./package.json ./yarn.lock ./
RUN yarn install
COPY . .
RUN yarn build

FROM nginx as web

EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
