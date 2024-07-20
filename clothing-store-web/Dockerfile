FROM node:14 AS build 

WORKDIR /app

#Install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application source code
COPY . . 

# build the angular application
RUN npm run build

# Stage 2: Serve the application using nginx
FROM nginx:alpine

# Copy the build artifacts from the build stage
COPY --from=build /app/dist/clothing-store-web /usr/share/nginx/html

# Copy a custom nginx configuration file (optional)
# COPY nginx.conf /etc/nginx/nginx.conf

# Expose prt 80
EXPOSE 80

# Command to run nginx
CMD ["nginx", "-g", "daemon off;"]
