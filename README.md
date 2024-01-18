# DITL
This repo syncs with CloudFormation to create a stack.

It will create a webserver with a basic page.

The webserver runs on port 80 on the instance's IP address.

## Problems

If you need to fix something you have to login with systems manager

```
aws ssm start-session --target <instance id>
```

### Webserver stopped
Login with ssm and restart the webserver

eg
```
systemctl start httpd
```

## Deployment

This is deployed from github.
If you want a local deployment:
```
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name ditl4 --template-body file://cfn.yaml
```
