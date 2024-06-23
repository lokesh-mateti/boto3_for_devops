Sure, here are 20 examples of how Boto3 can be used in various DevOps use cases:

1. **Launching an EC2 Instance:**
   ```python
   import boto3

   ec2 = boto3.client('ec2')
   ec2.run_instances(
       ImageId='ami-0abcdef1234567890',
       InstanceType='t2.micro',
       MinCount=1,
       MaxCount=1
   )
   ```

2. **Stopping an EC2 Instance:**
   ```python
   import boto3

   ec2 = boto3.client('ec2')
   ec2.stop_instances(InstanceIds=['i-0abcdef1234567890'])
   ```

3. **Creating an S3 Bucket:**
   ```python
   import boto3

   s3 = boto3.client('s3')
   s3.create_bucket(Bucket='my-new-bucket')
   ```

4. **Uploading a File to S3:**
   ```python
   import boto3

   s3 = boto3.client('s3')
   s3.upload_file('file.txt', 'my-bucket', 'file.txt')
   ```

5. **Downloading a File from S3:**
   ```python
   import boto3

   s3 = boto3.client('s3')
   s3.download_file('my-bucket', 'file.txt', 'file.txt')
   ```

6. **Listing S3 Buckets:**
   ```python
   import boto3

   s3 = boto3.client('s3')
   response = s3.list_buckets()
   for bucket in response['Buckets']:
       print(bucket['Name'])
   ```

7. **Creating a CloudFormation Stack:**
   ```python
   import boto3

   cloudformation = boto3.client('cloudformation')
   cloudformation.create_stack(
       StackName='my-stack',
       TemplateURL='https://s3.amazonaws.com/path-to-template/template.yaml'
   )
   ```

8. **Updating a CloudFormation Stack:**
   ```python
   import boto3

   cloudformation = boto3.client('cloudformation')
   cloudformation.update_stack(
       StackName='my-stack',
       TemplateURL='https://s3.amazonaws.com/path-to-template/template.yaml'
   )
   ```

9. **Deleting a CloudFormation Stack:**
   ```python
   import boto3

   cloudformation = boto3.client('cloudformation')
   cloudformation.delete_stack(StackName='my-stack')
   ```

10. **Listing CloudFormation Stacks:**
    ```python
    import boto3

    cloudformation = boto3.client('cloudformation')
    response = cloudformation.describe_stacks()
    for stack in response['Stacks']:
        print(stack['StackName'])
    ```

11. **Creating an IAM User:**
    ```python
    import boto3

    iam = boto3.client('iam')
    iam.create_user(UserName='new-user')
    ```

12. **Attaching a Policy to an IAM User:**
    ```python
    import boto3

    iam = boto3.client('iam')
    iam.attach_user_policy(
        UserName='new-user',
        PolicyArn='arn:aws:iam::aws:policy/AdministratorAccess'
    )
    ```

13. **Creating a Lambda Function:**
    ```python
    import boto3

    lambda_client = boto3.client('lambda')
    with open('function.zip', 'rb') as f:
        zipped_code = f.read()

    lambda_client.create_function(
        FunctionName='my-function',
        Runtime='python3.8',
        Role='arn:aws:iam::123456789012:role/my-role',
        Handler='lambda_function.lambda_handler',
        Code=dict(ZipFile=zipped_code)
    )
    ```

14. **Invoking a Lambda Function:**
    ```python
    import boto3

    lambda_client = boto3.client('lambda')
    response = lambda_client.invoke(
        FunctionName='my-function',
        InvocationType='RequestResponse',
        Payload=json.dumps({'key': 'value'})
    )
    ```

15. **Creating an RDS Instance:**
    ```python
    import boto3

    rds = boto3.client('rds')
    rds.create_db_instance(
        DBName='mydatabase',
        DBInstanceIdentifier='mydbinstance',
        AllocatedStorage=20,
        DBInstanceClass='db.t2.micro',
        Engine='mysql',
        MasterUsername='admin',
        MasterUserPassword='password'
    )
    ```

16. **Starting an RDS Instance:**
    ```python
    import boto3

    rds = boto3.client('rds')
    rds.start_db_instance(DBInstanceIdentifier='mydbinstance')
    ```

17. **Stopping an RDS Instance:**
    ```python
    import boto3

    rds = boto3.client('rds')
    rds.stop_db_instance(DBInstanceIdentifier='mydbinstance')
    ```

18. **Creating an ECS Cluster:**
    ```python
    import boto3

    ecs = boto3.client('ecs')
    ecs.create_cluster(clusterName='my-cluster')
    ```

19. **Registering a Task Definition in ECS:**
    ```python
    import boto3

    ecs = boto3.client('ecs')
    ecs.register_task_definition(
        family='my-task',
        containerDefinitions=[
            {
                'name': 'my-container',
                'image': 'nginx',
                'memory': 512,
                'cpu': 256,
                'essential': True,
                'portMappings': [
                    {
                        'containerPort': 80,
                        'hostPort': 80
                    }
                ]
            }
        ]
    )
    ```

20. **Running a Task in ECS:**
    ```python
    import boto3

    ecs = boto3.client('ecs')
    ecs.run_task(
        cluster='my-cluster',
        taskDefinition='my-task',
        count=1
    )
    ```

These examples cover a wide range of AWS services that are commonly used in DevOps scenarios, demonstrating how Boto3 can help automate and manage infrastructure, applications, and services.
