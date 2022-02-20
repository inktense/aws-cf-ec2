# aws-cf-ec2
CloudFormation template to create an EC2 instance with security groups.

Experimented using the following template components:

- Resources
- Parameters
- Mappings

## Commands
---------------------------------
Create the stack 
``` 
aws cloudformation deploy --template-file ec2.yaml --stack-name DemoEc2Stack --profile <PROFILE>
```


Failed to create/update the stack. Run the following command
to fetch the list of events leading up to the failure
```
aws cloudformation describe-stack-events --stack-name DemoEc2Stack --profile <PROFILE>
```

Deleting the stack 
```
aws cloudformation delete-stack --stack-name DemoEc2Stack --profile <PROFILE>
```

## Potential errors
--------------------------------

- **An error occurred (ValidationError) when calling the CreateChangeSet operation: Stack is in ROLLBACK_COMPLETE state and can not be updated.**

```
This happens when stack creation fails. By default the stack will remain in place with a status of ROLLBACK_COMPLETE. This means it's successfully rolled back (deleted) all the resources which the stack had created. The only thing remaining is the empty stack itself. You cannot update this stack; you must manually delete it, after which you can attempt to deploy it again.
```
