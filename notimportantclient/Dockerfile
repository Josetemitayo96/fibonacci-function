#setting up dockerfile for the react end
FROM node:alpine as builder 

WORKDIR '/app'

COPY ./package.json ./
RUN npm install

COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
#copying the default.conf file to the nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#copy the node image folder to the nginx folder
COPY --from=builder /app/build /usr/share/nginx/html