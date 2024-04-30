# development environment
FROM node:21-alpine as dev
WORKDIR /frontend
#ENV PATH /frontend/node_modules/.bin:$PATH
COPY package*.json .
RUN npm install
COPY . ./
RUN npm run build

# production environment
FROM nginx:stable-alpine as prod
COPY --from=dev /frontend/dist /usr/share/nginx/html
COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
