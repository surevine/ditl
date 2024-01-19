# DITL
This repo syncs with CloudFormation to create a stack.

It will create a webserver with a basic page.

The webserver runs on port 80 on the instance's IP address.

## Problems

If you need to fix something you have to login with systems manager

```
aws ssm start-session --target <instance id>
```
If you login to the AWS UI, top right hand corner there is a button like a command prompt in a box. Click it for "CloudShell" and all your key/secret/region etc. are ready setup.

### Webserver stopped
Login with ssm and restart the webserver

eg
```
systemctl start httpd
```

## Deployment

### Jira
Before deploying create a jiraurl SSM parameter.

This URL should be a webhook to an automation to create a ticket. The hook will supply summary and description fields.

Issue priorities range from 1 (highest) to 5 (lowest).

### GitHub
This is all automatically deployed from Github on changes to main branch.

If you want a local deployment:
```
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name ditl --template-body file://cfn.yaml
```

