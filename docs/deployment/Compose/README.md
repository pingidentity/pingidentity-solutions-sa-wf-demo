## Docker Compose deployment

### Pre-Requisites
* [Docker](https://www.docker.com/get-started)
* [Docker-Compose](https://docs.docker.com/compose/install/)
* [Ping DevOps - Compose](https://pingidentity-devops.gitbook.io/devops/deploy/deploycompose)

### Configuration Variables
Variables have been exposed to allow the deployment to be customized to your specific environment.  

The necessary variables are configured in 2 locations, depending on where they are applied:
* API Configuration: [Postman Variables](/docs/deployment-variables.md)
* Docker Images: [Image Variables](./environment-vars.md)

### Deployment - Docker Compose
* Copy the `docker-compose.yaml`, `env_vars` and `postman_vars.json` files to a folder
* Modify the `env_vars` file to match your environment
* Modify the `postman.json` file to match your environment
* Launch the stack with `docker-compose up -d`
* Logs for the stack can be watched with `docker-compose logs -f`
* Logs for individual services can be watched with `docker-compose logs -f {service}`
