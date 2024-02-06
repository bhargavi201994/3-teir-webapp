# Use an official Node.js image as a base image
FROM node:14-alpine

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run your application
CMD ["npm", "start"]



# Use an official OpenJDK image as a base image
FROM openjdk:openjdk-17-jdk

# Set the working directory
WORKDIR /app

# Copy the JAR file into the container
COPY target/*.jar app.jar

# Expose the port the app runs on
EXPOSE 8080

# Define the command to run your application
CMD ["java", "-jar", "app.jar"]

# Use an official PostgreSQL image as a base image
FROM postgres:latest

# Expose the default PostgreSQL port
EXPOSE 5432

# Environment variables for PostgreSQL configuration
ENV POSTGRES_DB postgres
ENV POSTGRES_USER postgresql
ENV POSTGRES_PASSWORD azureuser@123