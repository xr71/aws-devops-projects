# Microservices

## Function as a Service

Few lines of code that can be run based on events  
Machine learning prediction
We will look at AWS Lambda

Models for Serverless
Though we'll be using AWS cloud tools, there are a number of other providers that you can use to build serverless applications with auto-scaling capabilities. The skills you learn in this lesson will be widely applicable to these other platforms. Some of the larger, cloud providers include:

- Amazon Web Services [ Chalice & Cloud Formation]
- Terraform
- Google Cloud Platform
- Microsoft Azure

With all this, we can create an event driven architecture

### Cloud 9 and AWS Lambda

- the lambda handler takes in an event and context
- `lambda_handler(event, context)`
- create a new function
- add a trigger using API Gateway
- use an open HTTP gateway to test
- when responding with a json response, make sure to have
  - statusCode
  - headers
  - body

#### Docker Workflow in AWS Cloud 9

- make sure to set up a local SSH key in the C9 environment

```
ssh-keygen -t rsa
```

- goto your account settings in Github
- goto SSH and GPG keys
- New SSH key and paste in the public key
- now, make a connection to the repo from the remote server
- make a change like `echo "# Hello" >> README.md`
- make a commit and push
- create a Dockerfile
- build it locally
- tag it with unique id from AWS ECR (Amazon Container Services)
- push it to AWS ECR
