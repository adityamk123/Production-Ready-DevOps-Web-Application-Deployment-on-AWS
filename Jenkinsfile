pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "adityakhiroji/devops-portfolio"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/adityamk123/devops-portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-hub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {

                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop portfolio-container || true
                docker rm portfolio-container || true

                docker run -d -p 5000:5000 \
                --name portfolio-container \
                $DOCKER_IMAGE
                '''
            }
        }
    }
}

