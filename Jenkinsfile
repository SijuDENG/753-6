pipeline {
    agent any

    stages {
       
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
                script {
                    echo 'Deploying to Staging Environment'
                    withCredentials([file(credentialsId: 'asdfasdf', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                
                    }
                }
            }
        }

    stage('Integration Tests on Staging') {
        steps {
            script {
                // Replace the following lines with your specific integration test steps
                echo 'Running Integration Tests on Staging Environment'
                echo 'Add your specific integration test steps here'
                
            }
        }
    }

    stage('Deploy to Production') {
        steps {
            script {
                echo 'Deploying to Production Environment'
                withCredentials([file(credentialsId: 'asdfasdf', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                                    }
            }
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
