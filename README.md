# GitLab CloudFormation

## Installation

1. Ensure all yml files are up to date and accessible in S3. Change GitHub.yml addesses to reflect S3 URLs.

2. Use GitLab.yml to bring up a new CloudFormation stack. Make sure to make note of the database password when you create it.

3. Once the stack is finished, select the 'outputs' tab of the master stack in the CloudFormation console. Note the Redis, Postgres, and EFS endpoints.

4. SSH into the bastion, then into the GitLab 'test' instance and use the following documentation to install GitLab: https://about.gitlab.com/downloads-ee/#centos7

5. Follow instructions to mount the EFS filesystem here: https://docs.aws.amazon.com/efs/latest/ug/mounting-fs-mount-cmd-dns-name.html and make sure the setting persists on reboot using the documentation here: https://docs.aws.amazon.com/efs/latest/ug/mount-fs-auto-mount-onreboot.html

6. Subscribe relevant email to the GitLab SNS topic ARN from GitLab Control Stack output

7. Use the documentation here to configure GitLab: https://docs.gitlab.com/ee/README.html

8. Use the 'Test URL' from the CloudFormation Control stack outputs to verify your GitLab settings are functioning as you expect.

9. Create an AMI of the GitLab Test instance

10. Update the GitLab Control Stack in CloudFormation and supply the AMI ID of the image you just created to ApplicationImage parameter.

11. Log into the application using the 'Application URL' from the GitLab Control Stack output.

12. Shut down (Don't terminate!) 'GitLab Bastion' and 'GitLab Test Instance'

## Making changes to your GitLab deployment

Start 'GitLab Bastion' and 'GitLab Test Instance' and run through steps 7-12 of installation instructions again.

## Useful Documents:

https://docs.gitlab.com/omnibus/settings/nginx.html - The section on proxied SSL

https://docs.gitlab.com/omnibus/settings/configuration.html#storing-git-data-in-an-alternative-directory - Sending data to EFS

https://docs.gitlab.com/omnibus/settings/backups.html - Backup settings

https://docs.gitlab.com/omnibus/settings/ldap.html - LDAP settings

https://docs.gitlab.com/omnibus/settings/smtp.html - Email settings

https://docs.gitlab.com/ee/administration/high_availability/gitlab.html - Configure GitLab for HA (The intention of this repo)

https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/gitlab.yml.md - For help setting timezone

## Warnings:

Do not delete or modify any resource associated with the CloudFormation stack without using CloudFormation. This will cause the stack to enter a state in which it is unable to be updated via CloudFormation.
