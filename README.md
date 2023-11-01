# JENKINS-AWS
This repository will contain all jenkins project on AWS 


## Deploy Jenkin in ubuntu ec2 instance 
You first need to install jenkins by following the steps below or by going the official documentation Read [this page](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu) for more information about the syntax to use.

## Environment variable
`In steps 1` `INSTALL JAVA SDK` 
1. We first need to update the OS
```
sudo apt update

```
2. Then we install java package 
```
sudo apt install fontconfig openjdk-17-jre -y

```

`In steps 2`  `ADD JENKINS TO DEBIAN REPO`
1. We do this by using the Long term support release 
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

```
2. 
```
sudo apt install fontconfig openjdk-17-jre -y

```

`In steps 3` `INSTALL JENKINS`
1. We first update the libriaries 
```
sudo apt-get update

```
2. install jenkins  
```
sudo apt-get install jenkins -y

```
2. This command will check if jenkins has been install and working `DON'T FORGET TO COPY AND SAVE THE ADMIN PASSWORD` It may also be found  `/var/lib/jenkins/secrets/initialAdminPassword`
```
sudo systemctl status jenkins

```


Both `buildspec.yml` and `deployspec.yml` files are run in CodeBuild projects. Read [this page](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) for more information about the syntax to use.

*Important note:* in steps 2 and 5 you need to add `deployspec.yml` in `artifacts.files` section of the `buildspec.yml` among other output files in order for deployments to function.

```
artifacts:
  files:
    - ....
    - deployspec.yml
```

## CodeBuild role

If you need to perofm an action in your build or deployment phase which requires particular permissions you can add a [policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html) to the IAM role used by the CodeBuild projects. The role ARN is exported with this name: `${AWS::StackName}CodeBuildRoleArn`.

## Author
FOKOUE THOMAS 