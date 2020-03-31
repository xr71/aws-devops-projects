# Infrastructure as Code

- Create an IAM user for AWS CLI, I've named mine `awscli_user` for myself
- Make sure this user is AdminstratorAccess Groups Policy
- Take note of the Access and Secret Key: good practice is to rotate out the keys frequently

Use

```
aws cloudformation create-stack
--stack-name myfirsttest
--region us-west-2
--template-body file://filename.yml
```

After creating this stack, the next time, make sure to issue an `update-stack` command instead, never override existing resources
