# Use the official Node.js image with a specific version
# 'slim' images are smaller and more secure for production
FROM node:25.6.0-slim

# Set the working directory inside the container
# All subsequent commands (RUN, COPY, CMD) will execute here
WORKDIR /usr/app

# Copy package.json and package-lock.json first
# This leverages Docker layer caching: dependencies are only re-installed if these files change
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application source code to the container
COPY . .

# Execute the build script (compiles TypeScript/NestJS code to JavaScript)
RUN npm run build

# Inform Docker that the container listens on port 3000 at runtime
EXPOSE 3000

# Define the command to run the app in production mode
# Using the array syntax (exec form) is preferred for signal handling (e.g., SIGTERM)
CMD ["npm", "start"]