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
                script {
                    echo 'Deploying to Staging Environment'
                    withCredentials([file(credentialsId: 'your-gcp-credentials-id', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                    sh '''
                    gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                    gcloud config set project your-gcp-project-id
                    
                    # Replace the following lines with your specific staging GCP instance deployment steps
                    echo 'Deploying to staging GCP instance'
                    scp -i /path/to/your/key /path/to/your/application.war your-staging-gcp-instance-user@your-staging-gcp-instance-ip:/path/to/deployment/directory
                    ssh -i /path/to/your/key your-staging-gcp-instance-user@your-staging-gcp-instance-ip 'sudo systemctl restart your-application-service'
                    '''
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
                withCredentials([file(credentialsId: 'your-gcp-credentials-id', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                    sh '''
                    gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                    gcloud config set project your-gcp-project-id
                    
                    # Replace the following lines with your specific production GCP instance deployment steps
                    echo 'Deploying to production GCP instance'
                    scp -i /path/to/your/key /path/to/your/application.war your-production-gcp-instance-user@your-production-gcp-instance-ip:/path/to/deployment/directory
                    ssh -i /path/to/your/key your-production-gcp-instance-user@your-production-gcp-instance-ip 'sudo systemctl restart your-application-service'
                    '''
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
