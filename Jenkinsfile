pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/chayakruthi/springdemo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {

        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME}",
                body: "Build Successful",
                to: 'chayamanjappa@gmail.com'
            )
        }

        failure {
            emailext(
                subject: "FAILURE: ${env.JOB_NAME}",
                body: "Build Failed",
                to: 'chayamanjappa@gmail.com'
            )
        }
    }
}
