# cloudformation

aws cloudformation validate-template --template-body file://stack.yaml
aws cloudformation create-stack --stack-name eks-stack --template-body file://stack.yaml --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=EKSIAMRoleName,ParameterValue=eks-role ParameterKey=EKSClusterName,ParameterValue=eks-test-cluster

aws cloudformation delete-stack --stack-name eks-stack

nested 
aws cloudformation package --template-file template.yaml --output-template packaged.yaml --s3-bucket eks-deployment-bucket
aws cloudformation deploy --region us-east-2 --template-file packaged.yaml --stack-name EKS-dev --parameter-overrides EKSClusterName=devCluster-01 KeyName=schu-key NodeGroupName=devWorker01 Stage=dev --capabilities CAPABILITY_NAMED_IAM

aws eks update-kubeconfig --name devCluster-01