FROM node:18

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

#copy every other file inside app directory
COPY . . 

EXPOSE 5000

CMD ["node", "server.js"]




