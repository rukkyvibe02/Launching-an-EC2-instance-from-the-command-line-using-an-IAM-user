# Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user and Terminating the Instance
## Requirements
- AWS account
- AWS CLI installed and configured with IAM user credentials
- IAM user group with necessary permissions

My  login credentials from my Group Team Lead
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/d7749899-0a30-4ecb-9038-63db4cbe5815)
## STEP 1
- Install AWS CLI
- Run aws configure and input IAM user credentials (access key and secret key) along with default region settings.
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/f09d46cc-538f-4eeb-8e7a-a2ac59b9f5d7)
 successful configuration
## STEP 2
Create a Key Pair with the command line below:
- *aws ec2 create-key-pair --key-name (keypair-Name) --query 'KeyMaterial' –output text > (keypair-Name.pem)*
- aws ec2 create-key-pair --key-name eby --query 'KeyMaterial' --output text > rukky.pem
“rukky” is the unique key pair name.
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/27e54231-4fa5-427b-a582-23a15f0e093f)
  Key pair created successfully.
## STEP 3
Creating Security Group with the command line Below:
-	*input aws ec2 create-security-group --group-name (security group Name) --description (Description)*
-	aws ec2 create-security-group --group-name DeltaSecurityGroup --description "Delta security group"
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/35234f56-d2c3-42bd-a919-65d3e9957558)
- Security group created successfully
## STEP4
Allow SSH Port with command line below:
- *aws ec2 authorize-security-group-ingress --group-id (security group Id) --protocol tcp --port (port Number) --cidr (ip address)*
-	aws ec2 authorize-security-group-ingress --group-name DeltaSecurityGroup --protocol tcp --port 22 --cidr 0.0.0.0/0
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/9a9ca67a-d2c3-4fa7-94b3-9653b8b2c0db)
Successfully done.
## STEP 5
Launching the instance with command line below:
-	*aws ec2 run-instances --image-id (ami-Id) --count 1 --instance-type (type) --keyname (keypair-Name) --security-groups (security grp Name)*
-	aws ec2 run-instances --image-id ami-03a6eaae9938c858c --count 1 --instance-type t2.micro --key-name eby --security-groups DeltaSecurityGroup
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/5f7dbadf-1f6f-4057-ab2d-ce264fba30fa)
Ec2 Instance Launched Successfully.
## STEP 7
View instance on your AWS management console
-	Log in to your AWS account using your IAM user credentials.
-	In the AWS Management Console, search for "EC2" to access the EC2 Dashboard.
-	In the EC2 Dashboard, you'll find the "Instances" option, click on it to view your EC2 instances.
-	You'll find a list of launched instances, click on the one you just created and view the details by clicking on the description Botton.
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/fb328af3-c521-4b60-bf27-cbc684d4c67e)
Confirming the Launched instance from my console page. 
## STEP 8
Terminate running instance with command line below:
- *aws ec2 terminate-instances --instance-ids (Instance-Id)* 
- aws ec2 terminate-instances --instance-ids i-0f6ce6e30347c3550
![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/d0e1c92b-4a5c-4c83-9e09-b1a70de3c755)
Instance terminated successfully

![image](https://github.com/rukkyvibe02/Launching-an-EC2-instance-from-the-command-line-using-an-IAM-user/assets/146957698/19726758-bb8a-4c4a-a3df-b63afb8ad492)
Confirmation from your console page.

# The End!!!






















