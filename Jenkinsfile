pipeline {
    agent any

    stages {
        stage('ps') {
            steps {
                sh 'docker ps'
            }
        }
        
        stage('Cleanup') {
            steps {
                deleteDir() // Cleans workspace
            }
        }
        
        stage('git clone') {
            steps {
                sh 'git clone https://github.com/shubhamWithCode/docker-testapp.git'
            }
        }
        
        stage('docker build') {
            steps {
               dir('docker-testapp') {
                    sh 'docker build -t vickygaikwad41996/test-app .'
                }
            }
        }
        
        stage('docker push') {
            steps {
                //sh 'docker run -d -p 5050:5050 --name node-app vickygaikwad/test-app'
                sh 'docker login -u vickygaikwad41996@gmail.com -p Shubham@1234'
                sh 'docker push vickygaikwad41996/test-app'
            }
        }
        
    }
}