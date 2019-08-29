#!groovy
pipeline {
agent {label "master"}
parameters {
        choice(
        name: 'AWS_DEFAULT_REGION',
        choices: "us-west-1",
        description: 'aws_region' )
        
        choice(
        name: 'instance_type',
        choices: "t2.micro",
        description: 'type_of_instance' )
       
        string ( defaultValue: '', description: 'access_key_1', name: 'accessKeyVariable')
        string ( defaultValue: '', description: 'secret_key_1', name: 'secretKeyVariable')
        string ( defaultValue: '', description: 'pem_file', name: 'pem_file_name')
        }
    stages {
    stage ('Initialise Credentials') {
    steps {
    script {
        sh ''' ansible-playbook  -e "access_key=$accessKeyVariable" -e "secret_key=$secretKeyVariable" -e "aws_region=$AWS_DEFAULT_REGION" -e "insta_type=$instance_type" -e "key_pair=$pem_file_name" /home/jenuser/playbook/main.yml -vvv
 '''
             }
           }
		}
    }
}
