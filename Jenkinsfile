pipeline {
    agent any
    
    stages {
        stage('Build Docker images on Build Server') {
            steps {
                script {
                    // Execute Ansible playbook on Build Server
                    sh "ssh ubuntu@172.31.5.169 'ansible-playbook /home/ubuntu/build.yml'"                    // 'ansible-playbook /home/ubuntu/playbook.yaml'"
                
                    
                    }
            }
        }
        
        stage('Deploy Script on Deploy Server') {
            steps {
                script {
                    // Execute deployment playbook on Deploy Server
                    sh "ssh ubuntu@172.31.5.169 'ansible-playbook /home/ubuntu/deploy.yml'"
                }
            }
        }
    }
}

#this is a demo3 as recording failed
