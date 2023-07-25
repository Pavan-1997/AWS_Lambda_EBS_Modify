# AWS Lambda EBS Modify 

As a DevOps team, we take care AWS environment and make sure it is in place with the organization's policies. We use AWS CloudWatch and AWS Lambda to govern the resources accordingly to the policies. For example, we Trigger a Lambda function when an Amazon Block Storage (EBS) volume is created. We use Amazon CloudWatch Events that allows us to monitor and respond to EBS volumes that are of type GP2 and convert them to type GP3.

---
# EBS GP2 TO EBS GP3:

1. Create a AWS Lamba function which automatically create a IAM Role

    Give a function name
    Choose runtime as Python3.9
    You can test the default code source by click on test and provide a event


2. Create a cloud watch rule 
    
    Go to rules
    Create rule
    Service Name - EC2
    Event Type - EBS Volume Notification
    Select Specific Event - Choose create Volume
    Now add target - Lamba - select the Lamba funtion name created in Step 1.
    You can give rule name initially and description and click on create 

3. Verify to check Cloud Watch able to access Lamba by a dummy run

    Now go to EC2 - Volumes - Create volume - make sure its gp2 and create

4. Now check the Cloud Watch - Log groups 

    You will be getting a log stream - click on it and verify it has lambda

5. Now go to Lamba and write a Python code to convert GP2 to GP3 In the Repo

6. Attach Policy to the  IAM Role for accessing EBS resources

    Select the Lamba IAM Role
    Create a policy
    Choose the service - EC2
    Under actions allowed type volume - select DescribeVolume & ModifyVolume
    Select All resources in Resources
    Give a policy name 
    Click on create policy  

7. Now create a new volume it should be in GP3

    See the below attached image for the change the first volume without Lambda function and the second volume with Lambda function triggered.

![image](https://github.com/Pavan-1997/AWS_Lambda_EBS_Modify/assets/32020205/ae9230a8-da96-4f8c-9c7f-ec6fae56bdac)
