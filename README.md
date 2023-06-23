# private-isu-cloudformation-template
CloudFormation template for [private-isu](https://github.com/catatsuy/private-isu)

```bash
$ aws cloudformation create-stack \
  --stack-name $STACK_NAME \
  --template-body file://private-isu.yml \
  --parameters \
      ParameterKey=InstanceCount,ParameterValue=1 \
      ParameterKey=EnvironmentName,ParameterValue="PrivateIsucon" \
      ParameterKey=KeyName,ParameterValue="key-pair-name" \
      ParameterKey=SecurityGroupIds,ParameterValue="sg-XXXX\,sg-YYYY\,..." \
      ParameterKey=SubnetId,ParameterValue="subnet-XXXX"
$ aws cloudformation wait stack-create-complete --stack-name $STACK_NAME
$ aws cloudformation describe-stacks --stack-name $STACK_NAME --query 'Stacks[].Outputs' --output text
Bench	i-xxxxxxxxxxxxxxxxx
BenchIP	XX.XX.XX.XX
App1	i-xxxxxxxxxxxxxxxxx
App1IP	XX.XX.XX.XX
$ ssh -i /path/key-pair-name.pem ubuntu@XX.XX.XX.XX
```
