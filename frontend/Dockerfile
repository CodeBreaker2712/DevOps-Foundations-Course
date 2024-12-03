# Specify the base image
FROM node:23-alpine3.19

# Create the working directory
WORKDIR /frontend

# Copy package.json and package-lock.json, and install the dependencies
COPY package*.json .
RUN npm install

# Copy the frontend React code, and build the app for production
COPY . .
RUN npm run build

# Expose port 3000 for the frontend
EXPOSE 3000

# Start the React Dev Server when the container launches
CMD ["npm", "start"]