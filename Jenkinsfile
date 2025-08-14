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
        stage('Deploy to CloudHub 2.0') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypointplatform', usernameVariable: 'ANYPOINT_USERNAME', passwordVariable: 'ANYPOINT_PASSWORD')]) {
                    echo 'Deploying to CloudHub 2.0...'
                    bat "
                        mvn deploy -DmuleDeploy -DmuleVersion=4.9.0 ^
                        -Dusername=Chaithu08 ^
                        -Dpassword=Chaithu@516 ^
                        -Denvironment=Sandbox ^
                        -Dreplicas=1 ^
                        -DvCores=0.1 ^
                        -Dtarget=Cloudhub-US-East-2 ^
                        -Dprovider=MC
                    "
                }
            }
        }
    }
}
