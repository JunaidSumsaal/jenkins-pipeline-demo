pipeline {
    agent any

    stages {
        stage('Step 1: Environment Check') {
            steps {
                echo "Building on: ${env.NODE_NAME}"
                sh 'java -version'
                sh 'git --version'
            }
        }

        stage('Step 2: Build Simulation') {
            steps {
                echo 'Simulating application build...'
                // This creates a fake "app.txt" file
                sh 'echo "Build Version 1.0" > app.txt'
            }
        }

        stage('Step 3: Test Simulation') {
            steps {
                echo 'Running automated tests...'
                sh 'grep "Build Version" app.txt'
                echo 'Tests Passed ✅'
            }
        }

        stage('Step 4: Deployment') {
            steps {
                echo 'Deploying to Production...'
                sh 'ls -l app.txt'
            }
        }
    }

    // This block runs AFTER all stages
    post {
        always {
            echo 'I always run, no matter what! ✨'
        }
        success {
            echo 'Build Successful! Great job, Junaid! ✅'
        }
        failure {
            echo 'Build Failed! Check the logs above. ❌'
        }
    }
}
//junaid
//junaidddddddddd
