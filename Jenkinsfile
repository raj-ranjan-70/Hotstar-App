pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/guruteja1999/Hotstar-App.git'
            }
        }

        stage('build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Artifact') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: '6b6a87df-6251-491f-a569-4fb951689dd9',
                        path: 'http://13.60.94.86:8080'
                    )
                ],
                contextPath: 'hotstar-application',
                war: 'target/*.war'
            }
        }
    }
}
