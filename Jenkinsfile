pipeline {
    agent{
        docker{
            image 'node:10.24.0' //Image Docker Node.js
            args '-p 5001:5001'
        }
    }
    
    stages {        
        stage('Update npm '){
            steps {
                sh 'npm install -g npm@latest'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                
                sh 'npm test'
            }
        }
        stage('Run Application') {
            steps {
                // Execute the app
                sh 'npm start &'
                // wait 5 seconds to start appp
                sh 'sleep 60'
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}




















