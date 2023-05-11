## Restaurant web application

### Git clone

```
git clone https://github.com/victorpaxton/restaurant.git
```

```
cd restaurant
```

Let's create `Dockerfile` and `docker-compose.yml`

### Dockerfile

```
FROM node:18

WORKDIR /usr/src/app

COPY package* ./

RUN npm install
```

### docker-compose.yml

```
version: '3.8'

services:
  node-dev-env:
    build: . # Build with the Dockerfile here
    command: npm start # Run npm start as the command
    ports:
      - 3000:3000 # The app uses port 3000 by default, publish it as 3000
    volumes:
      - ./:/usr/src/app # Let us modify the contents of the container locally
      - node_modules:/usr/src/app/node_modules # A bit of node magic, this ensures the dependencies built for the image are not available locally.
    container_name: node-dev-env # Container name for convenience

volumes: # This is required for the node_modules named volume
  node_modules:


```

### Run

```
$ docker compose up
```

Test that the project is running by going to `http://localhost:3000`.

Ps: I use the MySQL for database, hope I can update setup for server and database soon.
