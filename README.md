# Quickstart

Disclaimer: The following is more notes than instructions. I'll try and tidy this up at some point.

1. Modify the rpmrepo.yml file to change all instances of AcmeCorp to your company name. Next create the Stack using CloudFormation.

```bash
aws cloudformation update-stack --stack-name rpmrepo --template-body file://rpmrepo.yml
```

2 Now, to build the repo and upload packages use something similar to the following:

```bash
yum install -y createrepo
mkdir ~/rpmrepo
```

3. Copy your RPM files in to the new directory. Then continue with generating the metadata and uploading the files.

```
createrepo ~/example-repo
aws s3 sync ~/rpmrepo s3://rpmrepo-acmecorp-{{randomid}}
```
