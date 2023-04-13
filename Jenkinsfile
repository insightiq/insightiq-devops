pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Test and Moving source code to Docker Swarm') {
            steps {
                sh 'ansible-playbook playbook-to-copy-data-to-docker.yml --user=jenkins'
            }
        }
        stage('Deploying the Containers') {
            steps {
                sh 'ansible-playbook playbook-for-deployment.yml --user=jenkins'
            }
        }
    }
}
