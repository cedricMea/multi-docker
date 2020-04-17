FROM node:alpine 
WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ ./
CMD ["npm", "run", "build"]

FROM nginx
# expose port 3000 specify in config file
EXPOSE 3000 
# copy nginx config file 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# copy the building file from first image
COPY --from=0 /app/build /usr/share/nginx/html