## TodoApp-Provision
This is the provisioning script for provisioning AWS resources for deploying TodoApp. You can find the link to app repository here
<https://github.com/pvsenan/TodoApp>

## Provisioning
Provisioning can be run as a Jenkins pipeline and for more information please see the Jenkinsfile under root folder

*IMPORTANT* The provisioning script uses Ansible, AWS Cloudformation and AWS Cli for performing the operations. Please make 
sure that the following is installed and configured in the jenkins server.
````yaml
python3
aws cli
aws eb cli
ansible
````
Jenkins pipeline config assumes that you
have set up the aws credentials in jenkins secret with the following ID
````yaml
    AWS_ACCESS
    AWS_SECRET
````
Pipeline uses manual approval process for provisioning Elastic Beanstalk and MySql database. Once the provisioning is completed
the database credentials for MySql can be found in the AWS secret manager under the name `todappdb-credentials`. This password can
later be added to the production properties file of the springboot application.