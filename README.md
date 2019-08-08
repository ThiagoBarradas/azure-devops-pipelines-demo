# Azure DevOps - Pipelines Demo

## All tools in this demo

- .NET Core 2.2 / xUnit (Application and tests)
- Azure DevOps (CI/CD)
- Sonarqube (Code quality analysis)
- Docker (Package / Containerization app)
- Docker Hub (Registry for docker images)
- Runscope (Integration tests)
- Azure (Infra to deploy)

## 1 - Appliciation development

- [Application](https://github.com/ThiagoBarradas/environment-api);
- Unit Tests;
- Dockerfile;
- All tests locally;

## 2 - Azure DevOps - Overview 

- [Create account and connect with GitHub](https://azure.microsoft.com/pt-br/services/devops/);
- Create a single project to aggregate applications;
- Create variable group in pipelines Library;

## 3 - Create Azure Build Pipeline

- [Predefined variables for Build Pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml)

## 3.1 - Create Build Step

- Create initial variables
- Create build step and commit; 
- See build results;
- Add store artifact;
- Commit and see results again;

[azure-pipelines.yml result](https://github.com/ThiagoBarradas/azure-devops-pipelines-demo/blob/master/build-pipelines/1-build.yml)

## 3.2 - Create Unit Tests Step

- Create tests step and commit; 
- See tests results;
- Add store artifact / publish code coverage and test results;
- Commit and see results again;

[azure-pipelines.yml result](https://github.com/ThiagoBarradas/azure-devops-pipelines-demo/blob/master/build-pipelines/2-build-test.yml)

## 3.3 - Create Quality Analysis Step

- [Install Sonarcloud Extension](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarcloud)
- [Register and setup project at Sonarcloud](https://sonarcloud.io)
- [Generate SonarCloud token and create a service connection in Azure DevOps](https://sonarcloud.io/account/security);
- Get `project_key` and service connection name and add to pipeline;
- Create QA step and commit;
- See results in Azure DevOps and SonarCloud;

[azure-pipelines.yml result](https://github.com/ThiagoBarradas/azure-devops-pipelines-demo/blob/master/build-pipelines/3-build-test-qa.yml)

## 3.4 - Create Docker Publish Step

- [Create account and create a project in Docker Hub](https://hub.docker.com)
- Create a service connection in Azure DevOps to connect with Docker Hub;
- [Conditions in Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/conditions?view=azure-devops&tabs=yaml)
- [Replace Tokens in Dockerfile using other Extension ](https://marketplace.visualstudio.com/items?itemName=qetza.replacetokens)
- Create PublishDocker step and commit;
- See new images in Docker Hub and run locally to check if new image works fine;

[azure-pipelines.yml result](https://github.com/ThiagoBarradas/azure-devops-pipelines-demo/blob/master/build-pipelines/4-build-test-qa-dockerpublish.yml)

## 4 - GitHub Status Check

- Create a new branch with some change and create a pull request;
- Check commit and PR build status;
- [See about skip CI build](https://docs.microsoft.com/en-us/azure/devops/pipelines/build/triggers?view=azure-devops&tabs=yaml)

## 5 - Badges

- Go to Azure DevOps Build Pipelines project dashboard and get your badge in top-right menu, 'Status Badge'
- Go to Sonarcloud Dashboard and click in 'Get Project Badges'
- Get badges for Quality Gate Status, Code Coverage
- Go to Shields.io to generate other badges for SonarCloud;
- Add in project README.md

[README.md badges result](https://github.com/ThiagoBarradas/azure-devops-pipelines-demo/blob/master/badges/badges.md)

## 6 - Prepare Infrastructure

- [Create a service using Azure App Service](https://portal.azure.com/#create/Microsoft.WebSite)
- [Swap Web App in Azure](https://docs.microsoft.com/pt-br/azure/app-service/deploy-staging-slots#to-rollback-a-production-app-after-swap)

## 7 - Create Azure Release Pipeline 

- [Predefined variables for Release Pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml)

## 7.1 - Create Deploy Step

- Create a single container/environment in Azure Web App
- [Simulate Deploy](https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/AzureAppServiceManageV0)
- Create Staging Environment
- Deploy to staging
- Then Swap Slots

## 4.1 - Create Integration Test Step

- Create Runscope Tests
- Install [Runscope Extension](https://marketplace.visualstudio.com/items?itemName=ThiagoBarradas.runscopetest)
- Setup Runscope Task

## 4.1 - Create Rollback Step

- If Runscope Test failed, swap again.
