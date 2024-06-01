# AWS B/S
CI/CD applied to ElasticBeanstalk and adjacent AWS tech

```shell
aws cloudformation validate-template --template-body file://application.cloudformation.yaml
aws cloudformation create-stack --stack-name eb1\
    --capabilities CAPABILITY_IAM\
    --on-failure DELETE\
    --template-body file://application.cloudformation.yaml
aws cloudformation wait stack-create-complete --stack-name eb1
aws cloudformation describe-stacks --stack-name eb1
```

# Sample Application B/S

```shell
aws s3 cp s3://elasticbeanstalk-samples-ap-southeast-2/java-sample-app.zip .
unzip java-sample-app.zip -d java-sample-app.d  # have a look at the contents
```

# CodePipeline B/S
    
```shell
aws cloudformation validate-template --template-body file://build.cloudformation.yaml
aws cloudformation create-stack --stack-name eb1build\
    --on-failure DELETE\
    --capabilities CAPABILITY_IAM\
    --parameters ParameterKey=elasticBeanstalkApplicationName,ParameterValue=eb1-ebApplication-ZZRS2DLEQ8VR\
                 ParameterKey=elasticBeanstalkEnvironmentName,ParameterValue=eb1-ebEnvi-nYLiKvB5Zw6x\
    --template-body file://build.cloudformation.yaml
```

```shell
aws cloudformation validate-template --template-body file://build.cloudformation.yaml
aws cloudformation update-stack --stack-name eb1build\
    --capabilities CAPABILITY_IAM\
    --parameters ParameterKey=elasticBeanstalkApplicationName,UsePreviousValue=true\
                 ParameterKey=elasticBeanstalkEnvironmentName,UsePreviousValue=true\
    --template-body file://build.cloudformation.yaml
```
