# codedeploy
DEPLOY A SIMPLE HTML APPLICATION TO EC2 INSTANCE FROM CODE COMMIT

PRE-REQUISITES:-

	Application code should be available in AWS Code-commit for this.
	IAM user account with full permissions for AWS code-commit, code-deploy, code pipeline, EC2 instance ----- As well as IAM permission. We need to create two roles.


THINGS TO KNOW:- 

	 AWS doesn’t allow to deploy directly into ec2 instance from code commit.
	Code deploy only has two options:  you can deploy directly only from S3 or GitHub.
	You can use your code and build it with AWS code-build. An artefact will be created. Store it in either S3 or GitHub. Then you can deploy it by the second step
	Only way to deploy the code stored in AWS code commit is through the AWS code pipeline

PROCEDURES:- 

	Create a role for AWS ec2 to access code deploy.

In roles – select the Ec2 then click add permissions search aws code deploy, give code deploy full permissions

	Create a role for AWS code deploy to deploy code into ec2.

In roles – select AWS code deploy – choose code deploy auto scaling then click add permission only one option will be there accept it and done.

	Create an EC2 instance in amazon Linux. Attach the first created role. Open the http, https tcp ports. And install the code deploy agent. Execute the codes in the file install agent.

	Create a code deploy application and choose Ec2/on premise. Create the deployment group and attach the second created role choose the ec2 instance. 

	Create the code pipeline let code commit to create a role, select the source as code commit. Skip the build stage. Choose code deploy group. Save it.

	The deployment will be done.

