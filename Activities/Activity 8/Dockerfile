FROM nginx
RUN apt update
COPY index.html /usr/share/nginx/html
EXPOSE 8085
CMD ["nginx","-g","daemon off;"]