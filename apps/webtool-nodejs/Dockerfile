#Build Stage
FROM node:24-alpine3.21 AS builder

#Adding Labels
LABEL name="JS WEBTOOL" \
    description="This is used as frontend Webtool" 

#Setup App Directory
WORKDIR /usr/src/app

#Copy Package List
COPY package*.json ./

#Install Packages/Dependencies
RUN npm ci --only=production

#Copy Source Code
COPY . .

#Production Stage
FROM node:24-alpine3.21

#Setup App Directory
WORKDIR /usr/src/app

#Copy Files from Builder Stage
COPY --from=builder /usr/src/app ./

#Expose Port
EXPOSE 3002

#Set User
USER node

#Run Application
CMD [ "npm", "run", "start" ]
