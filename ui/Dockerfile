#Using node as our base for the image
FROM node:12.6.0-alpine as build

#Setting our working dir to /app

WORKDIR /build

#Copying our dir into /build

COPY . .

#Updating apt

RUN NG_CLI_ANALYTICS=ci npm install
RUN NGI_CLI_ANALYTICS=ci npm install -g @angular/cli

RUN npm run build
RUN ls dist
#------------------------------------------------------------------------------------
FROM nginx:1.17.1-alpine

WORKDIR /app

COPY --from=build /build/dist/TeamAPoolProjectUI .

COPY nginx.conf /etc/nginx/nginx.conf

