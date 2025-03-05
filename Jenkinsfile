pipeline {
    agent any

    environment {
        GOOGLE_APPLICATION_CREDENTIALS = credentials('gcp_json')
    }

    stages {
      
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }

    post {
        success {
            echo 'Terraform Infrastructure Deployed Successfully!'
        }
        failure {
            echo 'Terraform Infrastructure Deployment Failed!'
        }
    }
}
