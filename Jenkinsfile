pipeline {
    agent any

    stages {
stage('Checkout') {
    steps {
        checkout scm
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
                        path: '',
                        url: 'http://16.171.175.116:8080'
                    )
                ],
                contextPath: 'hotstar-application',
                war: 'target/*.war'
            }
        }
    }
}
