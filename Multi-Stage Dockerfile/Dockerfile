# ---------- Stage 1: Build the React app ----------
FROM node:18 AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy rest of the project files
COPY . .

# Build the app for production
RUN npm run build


# ---------- Stage 2: Serve app using Nginx ----------
FROM nginx:alpine

# Copy build files from previous stage to Nginx HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
