FROM node:6-alpine
ADD . /npm
WORKDIR /npm
COPY package*.json ./npm
RUN npm install
EXPOSE 5555
CMD [ "npm", "start" ]
EOF