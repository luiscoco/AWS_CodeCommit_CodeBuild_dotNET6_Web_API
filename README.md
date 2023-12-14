# A simple tutorial to start working with AWS CodeCommit and CodeBuild .NET 6 Web API

**IMPORTANT NOTE!**: AWS CodeBuild only works with **.NET 6** but not it is not yet available for .NET 7 neither for .NET 8

## 1. Prerequisites

### 1.1. Grant AWSCodeCommitPowerUser permission to your user

Navigate to **AWS IAM** service and add permission to your user to work with AWS CodeCommit service

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/a3750070-f17f-44b1-8794-67471c72c3a3)

Click on **Users** menu option

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/acc165a5-1ae9-4de7-9b30-85717b867a0c)

Now we click on our user name, in my case "cloudUserLuis"

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/7fa3f0f4-d0e8-4ed1-8778-68349228369b)

We grant "**AWSCodeCommitPowerUser**" permission to your user

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/41379fb2-b5e0-4ef9-9528-4f9ec7f4972e)

### 1.2. Generate HTTPS Git credentials for AWS CodeCommit

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/0178e8f6-03a6-4f07-bc6b-3b66ca8fee76)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/5506be6e-754b-48bc-af36-3f09a538dfbd)

## 2. Create new code repository in AWS CodeCommit

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/08abbad0-39b7-4b53-beb5-b923d1460e4f)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/2058e177-42a5-4e51-b9c9-5dbda61f817e)

This is the AWS CodeCommit repo we created:

git clone **https://git-codecommit.eu-north-1.amazonaws.com/v1/repos/mydotnet6webapi**

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/4d418df6-0aa5-460a-b663-003b2ba22a43)

## 3. Create .NET 6 Web API in Visual Studio 2022

Run Visual Studio 2022 Community Edition and select the option **Create a new project**

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/4a3bf546-7af5-4fbd-b396-44717f640762)

We select the Web API project template

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/f433447b-f789-467a-9364-271570604284)

We set the solution name and location

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/9c5a22d4-1cab-4dba-9ede-57c2fb701f3e)

We select the options shown in the following picture

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/898ffe2a-14d8-469d-b610-25028910e60d)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/64dccce6-665c-4956-b88d-bf0bb8177593)

After creating the project we creat a new Git repo

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/3d051a09-81b9-402e-8ffd-946d6cf0fca3)

We copy the AWS CodeCommit repo URL in the Git repo URL: https://git-codecommit.eu-north-1.amazonaws.com/v1/repos/mydotnet6webapi

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/8efdc506-0f5a-44dd-a2ee-9d1a7fb38b9d)

## 4. Add the buildspec.yml file to the Web API application

We add a new buildspec.yml file in our project

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/f7a2fdc2-6f4f-4b83-9ad2-4595421e0125)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/d7b46e40-dcaa-407b-a829-d6dfbeaadee8)

This is the **buildspec.yml** file source code

```yaml
version: 0.2

phases:
  install:
    runtime-versions:
      dotnet: 6.0  # Updated to a supported version
  pre_build:
    commands:
      - echo Restoring solution
      - dotnet restore
  build:
    commands:
      - echo Build started on `date`
      - dotnet build -c Release
  post_build:
    commands:
      - echo Build completed on `date`
      - dotnet publish -c Release -o ./publish

artifacts:
  files:
    - '**/*'
  base-directory: './publish'

cache:
  paths:
    - '/root/.nuget/**/*'
```

## 5. Create AWS CodeBuild project

We press the "Create build project"

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/d7ae95de-bca9-44ee-8e8f-5d918057cb0f)

We set the AWS CodeBuild project name, we select the Source Provider AWS CodeCommit and finally we select the AWS CodeCommit repo 

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/b3938274-4ae6-4c17-890e-636d7b98ab19)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/2b713a5d-f778-4a74-a2f2-d55f83a9458f)

In this step we set the environment for building the solution. We select a Linux Ubuntu Virtual Machine. 

We also create a new service role for CodeBuild.

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/d93ac00d-6835-4f06-bdc5-6f99807f7f57)

It is time to specify the building commands, for this purpose we created in the above steps a buildspec.yml file. Now we confirm we are going to use the buildspec.yml file for building our solution.

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/cc71932e-a2ec-41cf-9e2a-1e9cc3efbc4d)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/728b8d2b-71b9-40f4-be92-95fb1972200b)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/42734826-4b3b-460a-b337-d38942c59eb6)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/6bf04079-8fba-45e5-82c6-2ca0e55824be)



