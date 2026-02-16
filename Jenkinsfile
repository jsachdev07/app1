pipeline {
    agent any
    tools {
        maven 'maven399'
    }

    stages {

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
    success {
        emailext(
            to: 'himanshusachdevpimr1517@gmail.com',
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build succeeded. Check console: ${env.BUILD_URL}"
        )
    }

    failure {
        emailext(
            to: 'himanshusachdevpimr1517@gmail.com',
            subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build failed. Check console: ${env.BUILD_URL}"
        )
    }
}
}
