FROM node:18-alpine AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:stable-alpine

# remove default config
RUN rm /etc/nginx/conf.d/default.conf

# add custom config
COPY nginx.conf /etc/nginx/conf.d/default.conf

# copy build files
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]