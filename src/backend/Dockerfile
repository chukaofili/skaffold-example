FROM node:12.16.2-alpine AS base
FROM base AS build

WORKDIR /www
COPY package*.json ./
RUN npm install

# copy node_modules from the build image
FROM base

WORKDIR /www
COPY --from=build /www/node_modules node_modules
ADD . /www

# Run app.js with debugging port and hotr-eloading when container launches
CMD ["npx", "nodemon", "--inspect=9229", "app.js"]

# Comment above and uncomment below to run app.js without debugger port and hotr-eloading when container launches
# CMD ["node", "app.js"]