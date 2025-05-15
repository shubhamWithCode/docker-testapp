pipeline {
    agent any

    // environment {
    //     DOCKER_IMAGE = 'your-dockerhub-username/your-node-app'
    //     DOCKER_CREDENTIALS_ID = 'docker-hub-credentials'
    // }

    stages {

        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/shubhamWithCode/docker-testapp.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t vickygaikwad41996/node-app .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker login -u vickygaikwad41996@gmail.com -p Shubham@1234'
                sh 'docker push vickygaikwad41996/node-app'
                }
            }
        }

        // stage('Deploy using Docker Compose') {
        //     steps {
        //         sh 'docker-compose -f Docker-compose.yaml $status'
        //     }
        // }

        stage('docker run'){
            steps{
                sh 'docker run -d -p 5050:5050 --name my-app vickygaikwad41996/node-app'
            }
        }

    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
