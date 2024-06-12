version: '3'
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: vue-app
    ports:
      - 8080:80
    depends_on:
      - nginx-agent
  nginx-agent:
    image: nginx:alpine
    container_name: nginx-agent
    environment:
      - API_KEY=1234567890abcdefghijkl
      - AMPLIFY_IMAGENAME=my_vue_app
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf
    ports:
      - 80:80
