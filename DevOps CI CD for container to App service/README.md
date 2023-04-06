# Tech-Articles

# CI/CD for Containers services based on Microservice architecture from Azure Devops to Azure Infrastructure.

Agenda: 
1.	Introduction
2.	Planning your CI/CD pipeline
3.	Setting up your Azure App Service environment
4.	Connecting your source control
5.	Configuring your build process
6.	Testing and validating your builds
7.	Deploying your microservices
8.	Monitoring and troubleshooting your pipeline
9.	Conclusion



## 1.	Introduction

>"DealStore" is a responsive web application with a web API in the background. The content, navigation elements, and structural layout of the website can be adapted to the screen resolution of the mobile device. The frontend was built using the Vue framework, a progressive JavaScript framework for creating web interfaces and one-page applications, to make the web application look modern and professional. An API gateway from Envoy is used as the interface between the frontend and the microservices. The backend of the  application was built using .NET 5, a framework for developing desktop, web, cloud, and mobile applications. The application uses a database that runs on the Azure Cloud and utilizes a MS SQL Server in a serverless manner.
>
>## DEAL, Provider and System microservice as backend and Frontend as a standalone service .
>
> The application uses three microservices, all of which run on Docker containers. The Deal-API manages service information such as adding/editing requests and adding/editing/searching services from companies. The Provider-API is an application programming interface that allows end-users to interact with the service. The System-API manages affected system configurations, email notifications, and log components.
>
> In this article, we'll delve into the details of how these components come together to form a successful microservice architecture, focusing on how to implement Continuous Integration and Continuous Deployment (CI/CD) for microservices on Azure App Service. By >the end of this article, you'll have a solid understanding of how to build a modern, professional, and scalable web application using microservices on Azure App Service.

### Clone the Article local
> git clone https://github.com/waelamer/Tech-Articles.git