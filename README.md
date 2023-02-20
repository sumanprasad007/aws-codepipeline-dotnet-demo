.NET Web Application CI/CD Pipeline using AWS CodePipeline

 
The Project provides a step-by-step guide for deploying an ASP.NET Core Web API to AWS Elastic Beanstalk using AWS CodePipeline. The prerequisites required for the deployment are an AWS account, Visual Studio or a preferred IDE, .NET 6.0+ SDK installed on the machine, and a GitHub account. The guide uses Visual Studio Community 2022 for the development process. The Project first creates a sample ASP.NET Core WebAPI 6.0 by creating a new project with the ASP.NET Core Web API template. The target framework is .NET 6, and the default Open API support is kept for later testing of the application once it's deployed.
Next, the Project creates a couple of minor changes. At the root of the solution, two new files named buildspec.yml and Procfile are created. The buildspec.yml file is used for building and publishing DLLs that can be deployed to AWS Elastic Beanstalk. The YAML file has four phases, including installing runtime, prebuild commands, build command, and post-build. The artifacts will point to the root directory.

The Procfile file is used by AWS Elastic Beanstalk to determine the entry point of the application when multiple DLLs are present at the root of the application source bundle. The Project also adds one line of code to the Program.cs file that maps a simple message to the root endpoint of the Web API.
After adding the required files and changes, the Project pushes this code to a brand new GitHub repository. The required application code is pushed to the GitHub Repository at the master branch.

Next, the Project creates an AWS ElasticBeanstalk environment and application by logging into the AWS account and navigating to AWS Elastic Beanstalk. A new web application is created with a nice name. The author selects .NET Core on the Linux platform. After the provisioning is completed, a URL is provided where the ASP.NET Core Web API is available.
Finally, the author creates an AWS CodePipeline step by step. The Project explains each step with screenshots, including the creation of an S3 bucket, a CodeBuild project, a CodePipeline, and how to configure AWS Elastic Beanstalk deployment. The Project concludes by explaining how to test the deployment and check the logs.
 

Creating an AWS CodePipeline – Step by Step:
Now that we have our application code pushed to the GitHub repository and the AWS Elastic Beanstalk environment is up and running, let’s create an AWS CodePipeline that would automate the process of deployment.
The AWS CodePipeline is a fully managed continuous delivery service that automates the build, test, and deploy phases of your release process every time there is a code change. Each time code is committed to a specified branch, the pipeline automatically builds and deploys the application.
	1. Go to the AWS Management Console, and navigate to the CodePipeline service.
	2. Click on the Create Pipeline button.
	3. Give the Pipeline a name and click on Next.
	4. On the next page, under the Source section, select GitHub and provide your GitHub credentials to allow AWS to access your GitHub repository. Once that is done, select the repository, branch, and change detection options as required.
	5. Click on Next to proceed to the Build section.
	6. Here, under the Build provider, select AWS CodeBuild and click on Create a new build project.
	7. Give the project a name, and select the Operating System as Ubuntu, Runtime as Standard, and the Image as aws/codebuild/standard:6.0. Once done, click on Continue.
	8. In the Environment configuration section, select the Compute type and the Environment Image, which will be used by the build.
	9. Next, under the buildspec section, select the Use a buildspec file option and specify the buildspec file that we created earlier. Make sure to select the correct location where the file is stored in the repository.
	10. Click on Create build project, and wait for it to be created.
	11. Once the build project is created, click on Next to proceed to the Deploy stage.
	12. Under the Deploy provider section, select AWS Elastic Beanstalk and select the region where the Elastic Beanstalk environment is created.
	13. Select the application and the environment that we created earlier and click on Next.
	14. Review the details of the pipeline, and click on Create pipeline.
	15. Once the pipeline is created, it will automatically start the build process. You can monitor the progress of the build and deployment by checking the pipeline’s progress.

Conclusion

In this Project, we have gone through the steps required to deploy an ASP.NET Core Web API to AWS Elastic Beanstalk using AWS CodePipeline. We started by creating a new project using Visual Studio, making the required changes to the solution, and pushing the code to GitHub.
Next, we created a new AWS Elastic Beanstalk environment, and then created an AWS CodePipeline to automate the build and deployment process. With the pipeline in place, each time a code change is pushed to the specified branch in the GitHub repository, the pipeline will automatically build and deploy the updated code to the Elastic Beanstalk environment. By automating the build and deployment process, we can ensure that the application is always up-to-date, and can quickly and easily roll back to previous versions if needed. The AWS CodePipeline service makes it easy to set up and manage the entire process, allowing developers to focus on writing code, rather than worrying about deployment.


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Deploying ASP.NET Core Web API to AWS Elastic Beanstalk using AWS CodePipeline

In this article, we are going to be deploying ASP.NET Core Web API to AWS Elastic Beanstalk using AWS CodePipeline. In the process, we will learn the basics of AWS Codepipeline, AWS CodeBuild, and AWS Elastic Beanstalk. This article is going to be a bit different from the other ‘Deploy .NET to AWS’ we had gone through earlier, as this will also get you started with CI/CD Pipelines on AWS!

By the end of the article, you will be having an AWS CodePipeline that can deploy your application to AWS ElasticBeanStalk whenever there is a new code push in your GitHub Repository.

![Deploying ASP.NET Core Web API to AWS Elastic Beanstalk using AWS CodePipeline](https://codewithmukesh.com/wp-content/uploads/2022/12/Deploying-ASP.NET-Core-WebAPI-to-AWS-Elastic-Beanstalk-using-AWS-CodePipeline-1.png)

## Topics covered
- What’s AWS Elastic Beanstalk?
- What’s AWS CodePipeline?
- What’s AWS CodeBuild?
- Understanding CI/CD with AWS
- Pushing Code to GitHub
- Creating an AWS ElasticBeanstalk Environment & Application
- Creating an AWS Codepipeline – Step by Step
- Exploring the AWS CodePipeline
- Setting Environment Variable in AWS Elastic Beanstalk

Read the Article: https://codewithmukesh.com/blog/deploying-aspnet-core-web-api-to-aws-elastic-beanstalk-using-aws-codepipeline/
