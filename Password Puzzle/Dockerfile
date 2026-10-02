# Multi-stage build for static site
FROM nginx:alpine AS base

# Set working directory
WORKDIR /usr/share/nginx/html

# Copy static assets
COPY index.html style.css image1.jpg ./

# Configure nginx
RUN echo 'server { listen 80; location / { root /usr/share/nginx/html; index index.html; } }' > /etc/nginx/conf.d/default.conf

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD wget --quiet --tries=1 --spider http://localhost/index.html || exit 1

# Expose port
EXPOSE 80

# Run nginx
CMD ["nginx", "-g", "daemon off;"]
