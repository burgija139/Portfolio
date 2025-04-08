# Use the official Node.js image for building the React app
FROM node:18 as build

# Set the working directory
WORKDIR /app

# Copy the frontend code
COPY . /app

# Install dependencies and build the React app
RUN npm install && npm run build

# Use an nginx image to serve the static files
FROM nginx:alpine

# Copy the built React app to the nginx html directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose the nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]