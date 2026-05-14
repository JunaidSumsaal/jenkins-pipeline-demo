pipeline {
    agent any
    
    stages {
        stage('Clone') {
            steps {
                echo '📥 Cloning repository...'
                sh 'pwd'
                sh 'ls -la'
            }
        }
        
        stage('Build') {
            steps {
                echo '🔨 Building...'
                sh 'echo "Build step executed from GitHub!"'
            }
        }
        
        stage('Test') {
            steps {
                echo '✅ Testing...'
                sh 'echo "All tests passed!"'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '🚀 Deploying...'
                sh 'echo "Deployment successful!"'
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}

// Testing webhook trigger junaid
