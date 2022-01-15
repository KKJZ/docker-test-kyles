# Docker React Test 

Repo for my learning docker with react found [here](https://mherman.org/blog/dockerizing-a-react-app/).

## Setup and Scripts

### Development Build Steps

#### Build Dockerfile

        docker build -t sample:dev .

#### Spin up container

        docker run \
            -it \
            --rm \
            -v ${PWD}:/app \
            -v /app/node_modules \
            -p 3001:3000 \
            -e CHOKIDAR_USEPOLLING=true \
            sample:dev

#### Compose

        docker-compose up -d --build

### Production build Steps

#### Build Dockerfile

        docker build -f Dockerfile.prod -t sample:prod .

#### Spin up container

        docker run -it --rm -p 1337:80 sample:prod

#### Compose

        docker-compose -f docker-compose.prod.yml up -d --build

### Heroku Settings

        heroku stack:set container -a <container-name>
        git push heroku main