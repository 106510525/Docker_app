# Use an official Node.js runtime as the base image
FROM node:14.17.0-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Expose the port your app runs on
EXPOSE 3000

# Command to run your application
CMD ["npm", "start"]
