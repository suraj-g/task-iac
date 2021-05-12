# ENDPOINT-URL
ENDPOINT URL:
http://54.190.172.115:80
=========================================

![image](https://user-images.githubusercontent.com/13271875/117990460-d1031200-b35a-11eb-8ae9-cb10bf8b4fe3.png)

**USAGE**
Edit terraform.tfvars. In particular, specify a valid AWS account.

Provision the infrastructure (and deploy the app on instance start):

terraform init; terraform apply --auto-approve
1.1) Case you change any part of the infrastructure, repeat step 1).

To tear down the infrastructure, run:

terraform init; terraform destroy --auto-approve

Notes
this module deploys one EC2 instance
upon start, the machine runs the deploy-hello-node.js script, which
pulls and runs the Hello-World docker app.
The instance is not configured with an SSH key, so logging into the instance is not possible.

The app is acessible via load-balancer DNS.
The app is accessible via instance public ip (will be removed in future versions).
AMI's are region specific
If you change the region, you must change the AMI
Destroy the resources as soon as you do not need them anymore

