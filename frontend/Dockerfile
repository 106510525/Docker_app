# Use a Node.js base image
FROM node:latest as builder

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the remaining application code to the container
COPY . .

# Build the application
RUN npm run build

# Use Nginx base image for serving the frontend
FROM nginx:alpine

# Copy the built artifacts from the previous stage to Nginx's public directory
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Command to run Nginx
CMD ["nginx", "-g", "daemon off;"]

