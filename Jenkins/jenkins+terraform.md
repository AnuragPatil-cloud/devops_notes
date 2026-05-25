## install aws cred plugin
## save aws keys to jenkins credentials
## create two stage pipeline like below
```groovy
pipeline {
    agent any

    stages {
        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/Rohit-1920/terraform-jenkins.git'
            }
        }
        stage('apply') {
            steps {
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-cred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                  sh '''terraform init
                    terraform validate
                    terraform apply --auto-approve'''
                }
            }
        }
    }
}
```
