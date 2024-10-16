pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t myapp .'
            }
        }
        stage('Test') {
            steps {
                // Run unit tests
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Push the Docker image to a container registry
                sh 'docker tag myapp myregistry/myapp:latest'
                sh 'docker push myregistry/myapp:latest'
                // Optionally, deploy to your cloud infrastructure
                // Example for AWS: 
                // sh 'aws ecs update-service --cluster my-cluster --service my-service --force-new-deployment'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
