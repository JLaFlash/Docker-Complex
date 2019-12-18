##***** build phase I
FROM node:alpine as builder
WORKDIR '/app'
COPY ./client/package.json .
RUN npm install
COPY . .
RUN npm run build
#*** /app/build/ <----- all the stuff we care about from the bill process

##***** RUN Phase II
FROM nginx
EXPOSE 3000
COPY /nginx/defult.conf /etc/nginx.conf.d/defult.conf
COPY --from=builder /app/build /usr/share/nginx/html

