FROM node:16-alpine

WORKDIR /app

ARG ATLAS_URI

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5050

ENV ATLAS_URI=${ATLAS_URI}

CMD ["npm", "run", "start"]