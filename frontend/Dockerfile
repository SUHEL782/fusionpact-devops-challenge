FROM nginx:stable-alpine  

# Copy frontend static files (nginx)
COPY . /usr/share/nginx/html

# Expose port
EXPOSE 80

# Run NGINX in foreground (must be used)
CMD ["nginx", "-g", "daemon off;"]

