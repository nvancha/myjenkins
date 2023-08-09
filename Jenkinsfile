pipeline {
    agent any
    stages {
        stage('Verify Terraform') {
            steps {
                // Check Terraform version to ensure it's installed
                sh 'terraform --version'
                // Print the current directory and list its contents for debugging
                sh 'pwd'
                sh 'ls -al'
            }
        }
        stage('git checkout') {
            steps {
                checkout scm
            }
        }
        stage('Terraform validate') {
            steps {
                // Validate Terraform configuration files
                sh 'terraform validate'
            }
        }
        stage('Terraform init') {
            steps {
                // Initialize Terraform with input set to false to prevent interactive prompts
                sh 'terraform init -no-color -input=false'
            }
        }
        stage('Terraform apply') {
            steps {
                // Apply Terraform configurations with detailed logging and input set to false
                sh 'TF_LOG=DEBUG terraform apply -auto-approve -no-color -input=false'
            }
        }
    }
}
