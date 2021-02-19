# Docker Build

What'sUp 24/7 has docker builds for both IOS and Windows platforms. Both builds are located in the [wu247docker repo](https://github.com/WhatsUp247/wu247docker). Depending on which platform you are using to contribute, please read the readme documentation carefully. If you see that there are some possible updates or improvements needed, create an issue with your questions or submit a pull request to the wu247docker repo for review.

## Build Files

All builds are using `docker-compose` with the declarations in the docker-compose.yml file. This file will look for a Dockerfile in each of the folders that you would be building.

To build or start your docker container, run the command:

```zsh
% docker-compose up -d
```

To shut down the docker container without deleting the container data, run the command:

```zsh
% docker-compose down
```
