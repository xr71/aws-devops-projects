# Deploying a High Availability Web App on AWS using Cloudformation

Your company is creating an Instagram clone called Udagram. Developers pushed the latest version of their code in a zip file located in a public S3 Bucket.

You have been tasked with deploying the application, along with the necessary supporting software into its matching infrastructure.

This needs to be done in an automated fashion so that the infrastructure can be discarded as soon as the testing team finishes their tests and gathers their results.

There will be two parts to this project:

- You'll first develop a diagram that you can present as part of your portfolio and as a visual aid to understand the CloudFormation script.
- The second part is to interpret the instructions as well as your own diagram and create a matching CloudFormation script.


## Files
Helper bash scripts to create and update our resources via the AWS CLI by using `aws cloudformation`. Make sure these scripts contain `CAPABILITY_IAM` and `CAPABILITY_NAMED_IAM` as our templates will be leveraging the creation of IAM policies and security groups
- create.sh
- update.sh

Templates and Parameters
- project-network.yml
- project-network-parameters.json
- project-servers.yml
- project-servers-parameters.json

Screenshots
- AWS High Availability Web App.png
- project-output-screenshot.png


## Instructions
1. Clone this repository
2. Make sure you have the `AWS CLI` tool installed (the files in this repo assume a UNIX-like environment)
3. Make sure to create a user in the console for your CLI that has `AdministratorAccess` permissions and configure your AWS CLI with the appropriate Access Key and Secret Key
4. Create an S3 bucket that stores the `udacity.zip` file which contains all of the web assets and html page for the Udagram app
5. Make sure the S3 bucket can be accessed by an automated Ec2 instance
6. Proceed to the next section to create the stacks


## Create Stacks
The infrastructure is devided in 2 Stacks. The **network** Stack sets up the required network-infrastructure. The **servers** Stack sets up the required server to deploy the application. It requires the network-Stack to be already running.

`1.` Create the network stack   
```./create_stack.sh mynetwork project-network.yml project-network-parameters.json```  
`2.` Create the servers stack<br>
```./create_stack.sh myservers project-servers.yml project-servers-parameters.json```  


### IMPORTANT: Make sure to use the AWS Console to delete all stacks created in this exercise in order to avoid ongoing costs