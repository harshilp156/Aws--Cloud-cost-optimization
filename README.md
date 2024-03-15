
# AWS Cloud Cost Optimization - Deleteing Stale Resources 

**Architecture**

The project demonstrates the automatic identification and deletion of stale Elastic Block Store (EBS) volume snapshots in an AWS environment. Stale snapshots can accumulate over time, leading to increased cloud storage costs and clutter. By implementing an AWS Lambda function triggered by CloudWatch EventBridge, the project ensures the timely identification and removal of these unnecessary snapshots, thus optimizing storage usage and reducing operational overhead.

![architecture](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/a5fd817e-01e4-4095-9b28-7bc3d3d3f180)

## Situation:

- AWS users often create snapshots of their Elastic Block Store (EBS) volumes for backup and disaster recovery purposes.
- Over time, these snapshots can become stale, taking up unnecessary storage space and incurring costs.
- AWS provides services like CloudWatch EventBridge and AWS Lambda to automate tasks like identifying and deleting stale snapshots.

## Task:

- Implement a Lambda function triggered by AWS CloudWatch EventBridge.
- The Lambda function should check for stale EBS volume snapshots and delete them automatically.

## Action:

1. Situation Analysis:

- Understand the need to manage EBS volume snapshots to avoid unnecessary costs and storage clutter.
2. Environment Setup:

- Set up an AWS account.
- Create an IAM role with permissions to manage EC2 instances, volumes, and snapshots.
- Set up an AWS Lambda function and configure it to be triggered by CloudWatch EventBridge.

3. Lambda Function Implementation:

- Write Python code for the Lambda function.
- Use the boto3 library to interact with AWS services.
- Define a lambda_handler function to receive events from CloudWatch EventBridge.
- Use the describe_snapshots method to get all EBS snapshots owned by the AWS account.
- Use the describe_instances method to get a list of active EC2 instances.
- Iterate through each snapshot and check if it's attached to any volume.
- If a snapshot is not attached to any volume or the volume is not attached to a running instance, delete the snapshot using the delete_snapshot method.

4. Testing and Deployment:

- Test the Lambda function with sample data to ensure it behaves as expected.
- Deploy the Lambda function to the AWS environment.
- Configure CloudWatch EventBridge to trigger the Lambda function at regular intervals.

## Result:

- Stale EBS volume snapshots are automatically identified and deleted, reducing storage costs and clutter in the AWS environment.
- The Lambda function runs efficiently, triggered by CloudWatch EventBridge, ensuring that the management of EBS snapshots is automated and hassle-free.
## Implementation 

EC2 : Free tier EC2 instance which automatically creates EBS volume.

![Screenshot (589)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/8e482956-68a7-49f3-8e7e-8c080b413ca5)

![Screenshot (590)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/ee33831b-7fc8-4d42-ab8c-0c1e8418eacf)






EBS snapshot: Taken snapshot of the EBS volume.

![Screenshot (591)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/5e18e726-190e-4347-963a-2a63d6874204)

![Screenshot (592)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/0746d4fb-822c-4d31-a15f-8d6b5aa6be89)

Lambda Function: Created lambda function with the python code which checks for the stale EBS volume snapshots and delete them.

![Screenshot (593)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/19591b4f-8d6f-48ec-8886-eaba74adeac4)

Attach IAM Role: Created IAM role to provide Lambda function access to the Describe snapshots, Delete snapshots, Describe volumes and Describe instances.

Cloud Watch: Created CloudWatch event bridge to trigger lambda function each day.

![Screenshot (598)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/77fb9999-d6c2-41d8-ae82-cbef6fc1899c)

Now I have deleted the EC2 instace along with the EBS volume.

![Screenshot (596)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/e60b4386-19e6-4469-b504-bd998cb21830)

As we can clearly see that the snapshot is also automatically deleted.

![Screenshot (597)](https://github.com/harshilp156/Aws-Cloud-cost-optimization/assets/67538347/56f4e978-327f-41d6-8ada-6e0ee48ba347)

## Tech Stack

**AWS:** EC2, IAM, EBS, CloudWatch, Lambda 

**Python**

**GIT**

