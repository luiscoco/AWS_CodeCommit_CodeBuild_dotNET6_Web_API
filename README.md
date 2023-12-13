# AWS CodeCommit CodeBuild .NET 6 Web API

## 1. Prerequisites

### 1.1. Grant AWSCodeCommitPowerUser permission to your user

Navigate to AWS IAM service and add permission to your user to work with CodeCommit

We have to grant "**AWSCodeCommitPowerUser**" permission

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/41379fb2-b5e0-4ef9-9528-4f9ec7f4972e)

### 1.2. Generate HTTPS Git credentials for AWS CodeCommit

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/0178e8f6-03a6-4f07-bc6b-3b66ca8fee76)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/5506be6e-754b-48bc-af36-3f09a538dfbd)

## 2. Create new code repository in AWS CodeCommit

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/08abbad0-39b7-4b53-beb5-b923d1460e4f)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/2058e177-42a5-4e51-b9c9-5dbda61f817e)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/4d418df6-0aa5-460a-b663-003b2ba22a43)

This is the AWS CodeCommit repo we created:

git clone https://git-codecommit.eu-north-1.amazonaws.com/v1/repos/mydotnet6webapi

## 3. Create .NET 6 Web API in Visual Studio 2022

Run Visual Studio 2022 Community Edition 

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/4a3bf546-7af5-4fbd-b396-44717f640762)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/f433447b-f789-467a-9364-271570604284)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/9c5a22d4-1cab-4dba-9ede-57c2fb701f3e)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/898ffe2a-14d8-469d-b610-25028910e60d)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/64dccce6-665c-4956-b88d-bf0bb8177593)

After creating the project we creat a new Git repo

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/3d051a09-81b9-402e-8ffd-946d6cf0fca3)

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/8efdc506-0f5a-44dd-a2ee-9d1a7fb38b9d)

## 4. Add the buildspec.yml file to the Web API application

We add a new buildspec.yml file in our project

![image](https://github.com/luiscoco/AWS_CodeCommit_CodeBuild_dotNET6_Web_API/assets/32194879/f7a2fdc2-6f4f-4b83-9ad2-4595421e0125)




## 5. Create AWS CodeBuild project



## 6. Create AWS CodeDeploy 


## 7. Create AWS Pipeline

