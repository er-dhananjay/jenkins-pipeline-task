pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-demo-app"
        CONTAINER_NAME = "jenkins-demo-container"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests inside container...'
                sh 'docker run --rm $IMAGE_NAME:latest node -e "require(\'./app\'); console.log(\'App loads OK\')"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container...'
                sh 'docker rm -f $CONTAINER_NAME || true'
                sh 'docker run -d --name $CONTAINER_NAME -p 3001:3000 $IMAGE_NAME:latest'
            }
        }
    }

    post {
        success { echo 'Pipeline succeeded!' }
        failure { echo 'Pipeline failed!' }
    }
}
