pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Building Docker Image"
                bat "docker build -t kubedemo ."
            }
        }

        stage('Docker Login') {
            steps {
                bat 'docker login -u sowmya959 -p Sowmyairuku@12'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                
                bat "docker tag kubedemo sowmya959/sample:kubeimage"
                bat "docker push sowmya959/sample:kubeimage"
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                
                bat 'kubectl apply -f deployment.yaml '
                bat 'kubectl apply -f service.yaml '
            }
        }
    }

    post {
        success {
            echo 'Successful'
        }
        failure {
            echo ' Failed'
        }
    }
}
