## Required plugins
pipeline:aws steps
s3 publisher
aws credentials

```groovy
pipeline {
    agent any
    stages {
        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/Rohit-1920/EasyCRUD-Updated.git'
            }
        }
        stage('build') {
            steps {
                sh '''cd backend
                    mvn clean package -DskipTests'''
            }
        }
        stage('s3upload') {
            steps {
              withAWS(credentials: 'creds', region: 'ap-south-1') {
    s3Upload(
        acl: 'Private',
        bucket: 'oncdec-online-b35-my-buxx',
        file: 'backend/target/student-registration-backend-0.0.1-SNAPSHOT.jar',
        path: 'backend/target/student-registration-backend-0.0.1-SNAPSHOT.jar'
    )
}
            }
        }
    }
}
```
