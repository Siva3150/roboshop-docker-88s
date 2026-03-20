FROM node:20.19.5-alpine3.21 as build 
EXPOSE 8080
WORKDIR /opt/server 
COPY package.json . 
COPY *.js . 
RUN npm install 


FROM node:20.19.5-alpine3.21
# Create a group and user
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
EXPOSE 8080
LABEL com.roboshop="roboshop" \
      component="catalogue" \
      created_by="siva" 
ENV MONGO="true" \ 
    MONGO_URL="mongodb://mongodb:27017/catalogue"
COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server
USER roboshop 
CMD ["server.js"]
ENTRYPOINT ["node" ]


# FROM node:20 
# EXPOSE 8080
# WORKDIR /opt/server 
# COPY package.json . 
# COPY *.js . 
# RUN npm install 
# ENV MONGO="true" \ 
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]