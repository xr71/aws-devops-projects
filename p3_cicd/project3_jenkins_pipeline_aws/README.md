# Project 3 Jenkins Pipeline in AWS

Setting up IAM as root:

- Create a new group in AWS IAM with access to
  - AmazonEC2FullAccess
  - AmazonVPCFullAccess
  - AmazonS3FullAccess
- Attach this group to a new user created in IAM with
  - Programmatic access
  - AWS Management Console access
- Sign in to `https://<your_aws_account_id>.signin.aws.amazon.com/console/` as the new IAM user

Create a new EC2 Instance:

- create a t2.micro
- create a security group in networking
  - allow SSH
  - allow port 8080 for Jenkins

Setup Jenkins:

```
apt update
apt upgrade
apt install default-jdk

wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt udpate
sudo apt install jenkins

sudo systemctl status jenkins
```

- after installing and starting Jenkins, install default plugins and install plugins related to Blue Ocean
- restart jenkins after Blue Ocean plugin install
- add a pipeline from Github
- make sure to authenticate with a token
- run your first pipeline
- click on Settings and navigate to `Scan Repository Triggers`
  - check the box for `Periodically if not otherwise run`
  - select every `2 minutes`

Set up AWS Credentials inside Jenkins

- on the left sidebar, click on `Credentials`
- Add credentials to the global scope

Set up S3 Bucket

- create a new s3 bucket
- enable it as a static hosting bucket
- update the Jenkins file to allow for S3 uploads
- make sure to install AWS and S3 related plugins

Install `tidy`

- `sudo apt install tidy`
- add the following to the Jenkinsfile: `tidy -q -e *.html`

Update the Jenkinsfile to sh Tidy

- the run will fail as the linting step in the pipeline if it finds incorrect html tags
- the run will pass if the html file passes linting
