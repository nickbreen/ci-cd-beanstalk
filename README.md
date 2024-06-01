# AWS B/S
CI/CD applied to ElasticBeanstalk and adjacent AWS tech

```shell
aws cloudformation validate-template --template-body file://application.yaml
aws cloudformation create-stack --capabilities CAPABILITY_IAM --on-failure DELETE --stack-name eb1 --template-body file://application.yaml
aws cloudformation wait stack-create-complete --stack-name eb1
aws cloudformation describe-stacks --stack-name eb1
```

# Python B/S

```shell
python3 -m venv .venv
. .venv/bin/activate
pip install awscli-local awscli
```

# LocalStack B/S

```shell
docker compose up --detach
```

```shell
docker compose down
```

```shell
awslocal cloudformation validate-template --template-body file://application.yaml
awslocal cloudformation create-stack --capabilities CAPABILITY_IAM --on-failure DELETE --stack-name eb1 --template-body file://application.yaml
awslocal cloudformation wait stack-create-complete --stack-name eb1
awslocal cloudformation describe-stacks --stack-name eb1
awslocal cloudformation describe-stack-events --stack-name eb1
```

# Sample Application B/S

```shell
aws s3 cp s3://elasticbeanstalk-samples-ap-southeast-2/java-sample-app.zip .
unzip java-sample-app.zip -d java-sample-app.d  # have a look at the contents
```

# CodePipeline B/S

```shell
aws codepipeline start-pipeline-execution --name eb1
```
