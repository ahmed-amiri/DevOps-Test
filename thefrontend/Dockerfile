# Use Node.js as the base image
FROM node:22-alpine as build

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json
COPY package.json package-lock.json ./

# Install the application dependencies
RUN npm install

# Copy the rest of the frontend code
COPY . /app

# Build the Angular application for production
RUN npm run build --prod

# Use Nginx to serve the production build
FROM nginx:alpine

# Copy the build output to Nginx's public directory
COPY --from=build /app/dist/thefrontend/browser /usr/share/nginx/html

# Expose the port the app will run on
EXPOSE 80

# Start Nginx to serve the app
CMD ["nginx", "-g", "daemon off;"]
