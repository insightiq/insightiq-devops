pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Copy source code to Docker swarm') {
            steps {
                sh 'ansible-playbook playbook-to-copy-data-to-docker.yml --user=jenkins'
            }
        }

        stage('Building and push new image to Docker hub') {
            steps {
                sh 'ansible-playbook ansible-playbook-to-push.yml --user=jenkins'
            }
        }

        stage('Deploying new Service in Docker Swarm') {
            steps {
                sh 'ansible-playbook playbook-for-deployment.yml --user=jenkins'
            }
        }
    }
}
