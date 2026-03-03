pipeline {
    agent any

    tools {
        maven 'Maven'   // Make sure Maven is configured in Jenkins Global Tools
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/kondal1989/SimpleWebApp.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                scp target/*.war ubuntu@http://3.147.74.219:8090/:/opt/tomcat/webapps/
                '''
            }
        }
    }
}
