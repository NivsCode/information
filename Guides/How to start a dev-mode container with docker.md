
### Start a dev-mode container with bind mounts
[Ref](https://docs.docker.com/get-started/06_bind_mounts/#start-a-dev-mode-container)

To run our container to support a development workflow, we will do the following:

-   Mount our source code into the container
-   Install all dependencies, including the “dev” dependencies
-   Start nodemon to watch for filesystem changes

```
docker run -dp 3000:3000 \
     -w /app -v "$(pwd):/app" \
     node:12-alpine \
     sh -c "yarn install && yarn run dev"
```


# Tags
#guide