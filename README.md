# action-deploy-container-to-registry

### Github Action to deploy docker container to DockerHub and Github Package Repository
 

  * Used in [Revive](https://github.com/sachinsshetty/revive) project to Deploy Dropwizard Docker Container at [Workflow](https://github.com/sachinsshetty/revive/blob/main/.github/workflows/push_docker_server_dropwizard.yml)

### Required Inputs :

  * docker-username:
  
    required: true
  
    description: "The secret key stored to deploy to docker hub"
  
  * docker-password:
  
    required: true
  
    description: "The secret password to deploy to docker hub"
  
  * project-name:
  
    required: true
  
    description: "Project name to publish image"  
  
  * service-name:
  
    required: true
  
    description: "Service name of image that is deployed" 
  
  * dockerfile-path:

    required: true
  
    description: "Path + Name of Dockerfile used to deploy container" 
  
  * github-actor:
  
    required: true
  
    description: "Username for github container" 
  
  * github-token:
  
    required: true
    
    description: "password for github container"
  
  * github-repository:
  
    required: true
  
    description: "Name of the github repository"



#### Example Inputs

  
    jobs:

      push_server_image :

        name : Push Docker image to Docker Hub - server

        runs-on : ubuntu-latest

        permissions:

          packages: write

          contents: read

        steps:

          - uses: actions/checkout@v3

          - name: deploy-container-to-registry

          - uses: slabstech/action-deploy-container-to-registry@v0.0.1

            with:

              docker-username: ${{ secrets.DOCKER_USERNAME }}

              docker-password: ${{ secrets.DOCKER_PASSWORD }} 

              github-actor: ${{ github.actor }}
          
              github-token: ${{ secrets.GITHUB_TOKEN }}
    
              github-repository: ${{ github.repository }}
          
              project-name: revive
    
              service-name: server-dropwizard
          
              dockerfile-path: ./docker/server/dropwizard/Dockerfile