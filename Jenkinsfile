pipeline {
    agent any
    environment {
    AWS_ACCESS_KEY_ID=credentials('AWS_ACCESS')
    AWS_SECRET_ACCESS_KEY=credentials('AWS_SECRET')
    }

    stages {
        stage('EB Provision') {
        input {
           message "Provision resources in AWS ?"
        }
        steps {
                sh 'echo Provisioning ElasticBeanstalk Environment..'
                sh 'ansible-playbook ansible.yml --tag elasticbeanstalk --extra-vars "ParamApplicationName=TodoApp ParamSpringProfilesActive=production ParamEnvironmentName=TodoApp-Env ParamHealthUrl=\'/actuator/health\' ParamSolutionStackName=\'64bit Amazon Linux 2 v3.2.4 running Corretto 11\'"'
        }
    }
        stage('DB Provision') {       
        input {
           message "Start provisioning database ?"
        }
        steps {
                sh 'echo Provisioning Database Environment..'
                sh 'ansible-playbook ansible.yml --tag rds --extra-vars "ParamDbName=todoappdb"'
        }
    }
    }
}