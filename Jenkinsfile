pipeline {
    agent any

    tools {
    maven 'Maven-3'
    jdk 'jdk-11'
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
                scp target/*.war ubuntu@3.145.99.11:/opt/tomcat/webapps/
                '''
            }
        }
    }
}
