FROM nginx:alpine-slim

# Custom Labels
LABEL maintainer="Carlosposada-dev"  
LABEL version="1.0"
LABEL description="A simple Nginx Application"
# OCI Labels
LABEL org.opencontainers.image.authors="Carlosposada-dev"
LABEL org.opencontainers.image.title="Add VS Copy"
LABEL org.opencontainers.image.description="A lightweight Nginx application built on Alpine."
LABEL org.opencontainers.image.version="2.0"
LABEL org.opencontainers.image.revision="1234567890abcdef" 
LABEL org.opencontainers.image.created="2025-07-30T22:15:00Z"
LABEL org.opencontainers.image.vendor="Cposada"
LABEL org.opencontainers.image.licenses="Nginx-2.0"

# Using COPY to copy a local file
COPY index.html /usr/share/nginx/html

# Using ADD with URL to download Docker LICENSE
ADD https://raw.githubusercontent.com/docker/cli/master/LICENSE /usr/share/nginx/html/docker-license.txt

# Using Add with tar files
ADD files.tar.gz /usr/share/nginx/html

# Using RUN to see the docker-license.txt file
RUN chmod -R a+r /usr/share/nginx/html/

