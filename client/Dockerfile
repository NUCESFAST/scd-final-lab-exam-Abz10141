# client/Dockerfile
# Use an official Node runtime as a parent image
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/20i0932_frontend

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the app
RUN npm run build

# Install serve to serve the app
RUN npm install -g serve

# Expose the port the app runs on
EXPOSE 0932

# Command to run the application
CMD ["serve", "-s", "build"]
