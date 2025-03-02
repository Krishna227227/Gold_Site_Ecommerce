pipeline {
    agent any

    stages {
        stage('Build Docker images on Build Server') {
            steps {
                script {
                    // Execute Ansible playbook on Build Server
                    sh "ssh ubuntu@172.31.23.107 'ansible-playbook /home/ubuntu/Gold_Site_Ecommerce/build.yml'"                    // 'ansible-playbook /home/ubuntu/playbook.yaml'"


                    }
            }
        }

        stage('Deploy Script on Deploy Server') {
            steps {
                script {
                    // Execute deployment playbook on Deploy Server
                    sh "ssh ubuntu@172.31.23.107 'ansible-playbook /home/ubuntu/Gold_Site_Ecommerce/deploy.yml'"
                }
            }
        }
        
        stage('SCM Checkout') {
            steps{
           git branch: 'main', url: 'https://github.com/Krishna227227/Gold_Site_Ecommerce.git'
            }
        }
        // run sonarqube test
        stage('Run Sonarqube') {
            environment {
                scannerHome = tool 'sonar';
            }
            steps {
              withSonarQubeEnv(credentialsId: 'sonar-token', installationName: 'sonar') {
                sh "${scannerHome}/bin/sonar-scanner"
              }
            }
        }
    
    }
}
