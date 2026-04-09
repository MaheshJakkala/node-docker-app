pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/MaheshJakkala/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t node-docker-app:${BUILD_NUMBER} .
                docker tag node-docker-app:${BUILD_NUMBER} maheshjakkala/node-docker-app:${BUILD_NUMBER}
                '''
            }
        }

        // stage('Push Docker Image') {
        //     steps {
        //         sh 'docker push maheshjakkala/node-docker-app:${BUILD_NUMBER}'
        //     }
        // }
        
        stage('Create container') {
            steps {
                sh 'docker run -d -p 3001:8080 maheshjakkala/node-docker-app:${BUILD_NUMBER}'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Testing Completed"'
            }
        }

         stage('Deployment') {
            steps {
                sh 'echo "Successfully Deployed"'
            }
        }



    }
}
