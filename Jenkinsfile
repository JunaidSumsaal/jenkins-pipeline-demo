pipeline {
    agent any

    options {
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Show Info') {
            steps {
                sh '''
                    echo "Current directory:"
                    pwd
                    echo ""
                    echo "Files:"
                    ls -lah
                    echo ""
                    echo "Git status:"
                    git status || true
                    echo ""
                    echo "Latest commit:"
                    git log -1 --oneline || true
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "Starting build..."
                    sleep 2
                    echo "Build completed successfully."
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Running tests..."
                    sleep 2
                    echo "Tests passed."
                '''
            }
        }
    }

    post {
        success {
            echo 'Build finished successfully.'
        }
        failure {
            echo 'Build failed. Check the console output.'
        }
        always {
            echo 'Pipeline run completed.'
        }
    }
}
