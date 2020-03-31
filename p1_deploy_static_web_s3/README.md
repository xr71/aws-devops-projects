# Deploying a Static Website to S3

Uses the following:

- S3 bucket creation
- S3 bucket configuration
- Website distribution via CloudFront
- Access website via web browser

### Step 1

We create a publicly available S3 bucket

### Step 2

We upload static file contents to this bucket

```bash
- css/
- img/
- vendor/
index.html
README.txt
```

### Step 3

Secure the bucket using IAM  
Enter the bucket policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AddPerm",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::your-website/*"]
    }
  ]
}
```

### Step 4

Configure S3 for Static Website delivery  
Click on `properties` and activate `Static web hosting` panel and use `index.html`

### Step 5

Distribute site using CloudFront  
First, create a `Distribution`  
Under `Origin Settings` select S3 bucket and use `/` to indicate root level  
Create the Distribution and wait for `DEPLOYED` status - navgiate to the domain name CloudFront created
