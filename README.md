# Collect_StudentData_with_HTML_S3_DynamoDB_LAMBDA_APIGateway
This project is to collect the student data like Student name, Student ID, Student Email, Program, Year,CertificationName, Certification Url, Vendor Name, Expiry Date with help of AWS Services like S3, DynamoDB, Lambda, API Gateway,IAM Roles

Step1:
Download the folder/ clone the repository

Step2:
Go to AWS Management Console
Select AWS S3 Service
Create a Bucket with ACL Enabled,Bucket Versioning enabled Enable Public Access
Now upload the index.html, error.html files in the bucket and make the files public using acl under actions
Under Properties enable static website hosting

Step3:
Select Lambda Service
Create a function with python run time
for intial lambda testing you can use test.py file
Deploy the function 
and create test event and configure the json with testevent.json

Step4:
Go to API Gateway Service
Select REST API and new API
Create a method with request type as "POST"
Integration Type "Lambda Fucntion"
Select the ARN of the lambda function for LAMBDA FUNCTION and create
Enable CORS under '/' with POST Option
Now Deploy API and copy the Invoke URL
Paste the Invoke URL in index.html at line 76
Now upload the updated index.html and again make it public using ACL under ACTIONS

Step5:
Select Dynamo DB Service
Create a Table with primary key "id"
Copy the Table ARN
Now move to Lambda Function
Configuration-> You can see a Role name ,click on it to move to IAM Service
Click add permisiion-> add inline policy
Now use JSON format for creating policy 
Copy paste the policy.txt data in IAM and update the Table ARN at line 15 and create

Step6:
Go to Lambda Function and update the python file with lambda.py file
Now deploy it and for testing update the event json with testevent1.json
Click test
Data is stored in Dynamo DB

Step7:
Finally click the static website hostig url to view the webpage with student data form
Fill the form and click submit
The data is stored in Dynamo DB.


