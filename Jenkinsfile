pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -f C:\\Users\\asas3\\OneDrive\\Desktop\\753\\Code\\DeakinWeb\\753-6\\pom.xml clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                bat 'mvn -f C:\\Users\\asas3\\OneDrive\\Desktop\\753\\Code\\DeakinWeb\\753-6\\pom.xml test'
            }
        }

        stage('Code Analysis') {
            steps {
                bat 'mvn -f C:\\Users\\asas3\\OneDrive\\Desktop\\753\\Code\\DeakinWeb\\753-6\\pom.xml checkstyle:checkstyle'
            }
        }

        stage('Security Scan') {
            steps {
                bat 'mvn -f C:\\Users\\asas3\\OneDrive\\Desktop\\753\\Code\\DeakinWeb\\753-6\\pom.xml verify'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Add your specific deployment steps here, e.g., using AWS CLI or Jenkins plugins'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Add your specific integration test steps here'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Add your specific deployment steps here, e.g., using AWS CLI or Jenkins plugins'
            }
        }
    }

    post {
        success {
            emailext attachLog: true,
                     body: 'success',
                     subject: 'success',
                     to: 's222376251@deakin.edu.au'
        }
        failure {
            emailext attachLog: true,
                     body: 'failure',
                     subject: 'failure',
                     to: 's222376251@deakin.edu.au'
        }
    }
}