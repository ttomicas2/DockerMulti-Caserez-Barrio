FROM node as builder

WORKDIR /app

COPY package.json .
COPY package-lock.json ./

RUN npm install
COPY . .
RUN npm run build

#FROM nginx:1.19-alpine
#COPY --from=build /app/public /usr/share/nginx/html

FROM node as production

WORKDIR /app

COPY --from=builder /app/build ./build

RUN npm install --production 

EXPOSE 3000

CMD ["node", "build"]