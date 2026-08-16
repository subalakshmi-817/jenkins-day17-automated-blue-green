pipeline {

    agent any

    environment {
        BLUE_IMAGE = "day17-blue"
        GREEN_IMAGE = "day17-green"

        BLUE_CONTAINER = "day17-blue-container"
        GREEN_CONTAINER = "day17-green-container"

        BLUE_PORT = "8091"
        GREEN_PORT = "8092"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
            }
        }

        stage('Build Blue Image') {
            steps {
                sh 'docker build -t ${BLUE_IMAGE} ./blue'
            }
        }

        stage('Build Green Image') {
            steps {
                sh 'docker build -t ${GREEN_IMAGE} ./green'
            }
        }

        stage('Remove Old Containers') {
            steps {
                sh '''
                docker rm -f ${BLUE_CONTAINER} || true
                docker rm -f ${GREEN_CONTAINER} || true
                '''
            }
        }

        stage('Deploy Blue') {
            steps {
                sh '''
                docker run -d \
                --name ${BLUE_CONTAINER} \
                -p ${BLUE_PORT}:80 \
                ${BLUE_IMAGE}
                '''
            }
        }

        stage('Health Check Blue') {
            steps {
                sh '''
                sleep 3
                curl -f http://localhost:${BLUE_PORT}
                '''
            }
        }

        stage('Deploy Green') {
            steps {
                sh '''
                docker run -d \
                --name ${GREEN_CONTAINER} \
                -p ${GREEN_PORT}:80 \
                ${GREEN_IMAGE}
                '''
            }
        }

        stage('Health Check Green') {
            steps {
                sh '''
                sleep 3
                curl -f http://localhost:${GREEN_PORT}
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                echo "Checking running containers..."
                docker ps

                echo "Checking Blue..."
                curl -f http://localhost:${BLUE_PORT}

                echo "Checking Green..."
                curl -f http://localhost:${GREEN_PORT}
                '''
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Day 17 automated Blue-Green deployment completed.'
        }

        failure {
            echo 'FAILURE: Day 17 Blue-Green deployment failed.'
        }
    }
}
