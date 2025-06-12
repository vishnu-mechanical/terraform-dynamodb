pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-key')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/vishnu-mechanical/terraform-dynamodb.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -var="aws_access_key=${AWS_ACCESS_KEY_ID}" -var="aws_secret_key=${AWS_SECRET_ACCESS_KEY}"'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve -var="aws_access_key=${AWS_ACCESS_KEY_ID}" -var="aws_secret_key=${AWS_SECRET_ACCESS_KEY}"'
            }
        }
    }
}
