pipeline{
    agent any
    environment{
        PATH="/opt/apache-maven-3.8.5/bin:$PATH"
    }
    stages{
        stage('SCM Checkout'){
            steps{
                git branch: 'main', credentialsId: '14a3ce24-2b36-4a50-b3c9-90cda70cbea7', url: 'https://github.com/ArinPaul/Task.git'
            }
        }
        stage('Build'){
            steps{
                sh "mvn clean install"
            }
        }
        stage('Deploy'){
            steps{
                ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'Ansible-Server', inventory: '/etc/ansible/hosts', playbook: '/etc/ansible/deploy.yml'
            }
        }
    }
}
