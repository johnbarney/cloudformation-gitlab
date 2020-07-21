# GitLab CloudFormation

The goal of this project is to make deploying GitLab to AWS easier.

## Templates

* *gitlab.yaml* - Deploys GitLab stack
* *gitlab-runner-pod.yaml* - Deploys a GitLab Runner pod
* *gitlab-runner-target-role.yaml* - Deploys role to target account allowing runners to deploy in multi-account scenarios

## GitLab Installation

NOTE: Currently no clustering support in this template.

Deploy gitlab.yaml to your preferred region.

Specifically the AMI parameter should be your favorite distribution. 

## Useful Documents:


