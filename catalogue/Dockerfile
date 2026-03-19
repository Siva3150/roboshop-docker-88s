FROM node:20.19.5-alpine3.21 as build 
EXPOSE 8080
WORKDIR /opt/server 
COPY package.json . 
COPY *.js . 
RUN npm install 


FROM node:20.19.5-alpine3.21
WORKDIR /opt/server
EXPOSE 8080
ENV MONGO="true" \ 
    MONGO_URL="mongodb://mongodb:27017/catalogue"
COPY --from=build /opt/server /opt/server 
CMD ["node", "server.js"]


# FROM node:20 
# EXPOSE 8080
# WORKDIR /opt/server 
# COPY package.json . 
# COPY *.js . 
# RUN npm install 
# ENV MONGO="true" \ 
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]