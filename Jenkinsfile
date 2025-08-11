pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Application is in Building Phase'
                bat 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo 'Application is in Testing Phase'
                bat 'mvn test'
            }
        }
        stage('cloudhub2Deployment') {
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypointplatform')
            }
            steps {
                bat 'mvn deploy -DmuleDeploy -DmuleVersion=4.9.0 -Dusername=Chaithu08 -Dpassword=Chaithu@516 -Dreplicas=1 -DvCores=0.1 -Dtarget=Cloudhub-US-East-2'
'
            }
        }
    }
}
