# Use a base image with Node.js installed
FROM node:16-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json files
Copy package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Application
RUN npm run build

# Use a lightweight Nginx base imagefor runtime
FROM nginx:alpine

# Copy the build React app from the previous stage
Copy --from=build /app/build /usr/share/nginx/html

# Expose port
EXPOSE 80

#command to start Nginx
CMD [ "nginx", "-g", "daemon off;" ]