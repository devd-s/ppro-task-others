# Use a minimal base image
FROM nginx:1.21.6-alpine

# Set a secure user instead of running as root
USER nginx

# Use a non-root user with limited permissions for better security
RUN mkdir -p /var/cache/nginx && chown -R nginx:nginx /var/cache/nginx

# Copy custom configuration files (if needed, to keep things simple I am not changing anything for now)
# COPY ./my-custom-nginx.conf /etc/nginx/nginx.conf

# Expose the default port
EXPOSE 80

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]

