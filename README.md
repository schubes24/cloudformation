# cloudformation

aws cloudformation validate-template --template-body file://stack.yaml
aws cloudformation create-stack --stack-name eks-stack --template-body file://stack.yaml --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=EKSIAMRoleName,ParameterValue=eks-role ParameterKey=EKSClusterName,ParameterValue=eks-test-cluster