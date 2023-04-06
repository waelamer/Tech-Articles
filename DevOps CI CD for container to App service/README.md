
# Tech-Articles | Simplifying CI/CD Container-Based Microservices with Azure DevOps and Azure Infrastructure.

Agenda: 
1.	Introduction
2.	Planning CI pipeline
3.	Setting up Azure App Service environment
4.	Deploying CD build process
5.	Conclusion



## 1.	Introduction

>"DealStore" is a responsive web application with a web API in the background. The content, navigation elements, and structural layout of the website can be adapted to the screen resolution of the mobile device. The frontend was built using the Vue framework, a progressive JavaScript framework for creating web interfaces and one-page applications, to make the web application look modern and professional. An API gateway from Envoy is used as the interface between the frontend and the microservices. The backend of the  application was built using .NET 5, a framework for developing desktop, web, cloud, and mobile applications. The application uses a database that runs on the Azure Cloud and utilizes a MS SQL Server in a serverless manner.
>
>#### DEAL, Provider and System microservice as backend and Frontend as a standalone service .
>
> The application uses three microservices, all of which run on Docker containers. The Deal-API manages service information such as adding/editing requests and adding/editing/searching services from companies. The Provider-API is an application programming interface that allows end-users to interact with the service. The System-API manages affected system configurations, email notifications, and log components.
>
> In this article, we'll delve into the details of how these components come together to form a successful microservice architecture, focusing on how to implement Continuous Integration and Continuous Deployment (CI/CD) for microservices on Azure App Service. By >the end of this article, you'll have a solid understanding of how to build a modern, professional, and scalable web application using microservices on Azure App Service.



## 2. Planning your CI/CD pipeline

>Each microservice folder should contain a Dockerfile for building the container. <br />
    -To set up the CI portion of the pipeline for the DealStore application, an Azure Container Registry needs to be created where the container images will be stored. <br />
    -The build environment needs to be configured, including creating a build agent pool and specifying the tools and dependencies required to build each container image. <br />
    -Each microservice folder should contain a Dockerfile, which specifies how the container image for that service should be built. <br />
    -A build definition for each microservice needs to be created, which specifies the steps and configurations required to build the container image for that service. <br />
    -Continuous integration can be set up to automatically trigger a build when changes are pushed to the source control repository, automating the build process. <br />
    -Once the container image has been built, it can be pushed to the Azure Container Registry for storage and deployment. <br />
>By following these steps, a streamlined and automated CI pipeline for the DealStore application can be set up on Azure App Service. <br />

```yaml
yaml: 
pool:
  name: Azure Pipelines
steps:
- task: AzureResourceGroupDeployment@2
  displayName: 'Azure Deployment:Create Azure Container Registry'
  inputs:
    azureSubscription: 'DealStoreContainer - Azure'
    resourceGroupName: 'DealStoreContainer-rg'
    location: 'South Central US'
    templateLocation: 'URL of the file'
    csmFileLink: 'https://raw.githubusercontent.com/Microsoft/devops-project-samples/057f6cc268a62922d012067d069d58684e967d0a/armtemplates/webapp-containers/containerRegistry-template.json'
    overrideParameters: '-registryName "DealStoreContaineracr" -registryLocation "South Central US" -registrySku "Standard"'

- task: Docker@2
  displayName: 'Deal Microservice buildAndPush'
  inputs:
    containerRegistry: Deal
    repository: DealRepo
    Dockerfile: Backend.Deal/Dockerfile

- task: Docker@2
  displayName: 'Provider Microservice buildAndPush'
  inputs:
    containerRegistry: Deal
    repository: ProviderRepo
    Dockerfile: Backend.Provider/Dockerfile

- task: Docker@2
  displayName: 'System Microservice buildAndPush'
  inputs:
    containerRegistry: Deal
    repository: SystemRepo
    Dockerfile: Backend.System/Dockerfile

- task: Docker@2
  displayName: 'Frontend Microservice buildAndPush'
  inputs:
    containerRegistry: Deal
    repository: FrontendRepo
    Dockerfile: Frontend/Dockerfile
```



#### STEP 1
![Step 1](imgs/CI_1.png)

#### STEP 2
![Step 2](imgs/CI_2.png)

#### STEP 3
![Step 3](imgs/CI_3.png)

#### STEP 4
![Step 4](imgs/CI_4.png)

#### STEP 5
![Step 5](imgs/CI_5.png)

#### STEP 6
![Step 6](imgs/CI_6.png)

#### STEP 7
![Step 7](imgs/CI_7.png)

#### STEP 8
![Step 8](imgs/CI_8.png)


### Clone the Article local
> git clone https://github.com/waelamer/Tech-Articles.git