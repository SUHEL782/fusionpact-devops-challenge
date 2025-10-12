FROM nginx:stable-alpine

# Copy frontend static files
COPY . /usr/share/nginx/html

# Expose port
EXPOSE 80

# Run NGINX in foreground
CMD ["nginx", "-g", "daemon off;"]

