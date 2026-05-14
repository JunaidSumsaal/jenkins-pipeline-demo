pipeline {
    agent any
    
    options {
        // Keep last 10 builds
        buildDiscarder(logRotator(numToKeepStr: '10'))
        // Add timestamps to console output
        timestamps()
    }
    
    environment {
        // Set environment variables
        BUILD_INFO = "Build #${BUILD_NUMBER} - ${env.GIT_BRANCH}"
        TIMESTAMP = sh(script: "date '+%Y-%m-%d %H:%M:%S'", returnStdout: true).trim()
    }
    
    stages {
        stage('🔍 Checkout Code') {
            steps {
                echo "═══════════════════════════════════════════"
                echo "📦 CHECKING OUT CODE FROM GITHUB"
                echo "═══════════════════════════════════════════"
                echo "⏰ Timestamp: ${TIMESTAMP}"
                echo "🔗 Branch: ${env.GIT_BRANCH}"
                echo "📍 Commit: ${env.GIT_COMMIT}"
                
                checkout scm
                
                echo "✅ Code checked out successfully!"
            }
        }
        
        stage('📋 Display Repository Info') {
            steps {
                echo "═══════════════════════════════════════════"
                echo "📊 REPOSITORY INFORMATION"
                echo "═══════════════════════════════════════════"
                
                sh '''
                    echo "Current directory: $(pwd)"
                    echo "Files in workspace:"
                    ls -lah
                    echo ""
                    echo "Git status:"
                    git status
                    echo ""
                    echo "Latest commit:"
                    git log -1 --oneline
                '''
                
                echo "✅ Repository info displayed!"
            }
        }
        
        stage('🏗️ Build') {
            steps {
                echo "═══════════════════════════════════════════"
                echo "🔨 STARTING BUILD PROCESS"
                echo "═══════════════════════════════════════════"
                
                sh '''
                    echo "Build started at: $(date)"
                    echo "Building application..."
                    
                    # Example: Build commands (modify as needed)
                    # npm install
                    # npm run build
                    
                    echo "Simulating build process..."
                    sleep 2
                    echo "✅ Build completed successfully!"
                '''
            }
        }
        
        stage('🧪 Test') {
            steps {
                echo "═══════════════════════════════════════════"
                echo "🧪 RUNNING TESTS"
                echo "═══════════════════════════════════════════"
                
                sh '''
                    echo "Running tests..."
                    
                    # Example: Test commands (modify as needed)
                    # npm test
                    
                    echo "Simulating test process..."
                    sleep 2
                    echo "✅ All tests passed!"
                '''
            }
        }
        
        stage('📦 Package/Deploy') {
            steps {
                echo "═══════════════════════════════════════════"
                echo "📦 PACKAGING/DEPLOYMENT"
                echo "═══════════════════════════════════════════"
                
                sh '''
                    echo "Packaging application..."
                    
                    # Example: Package commands (modify as needed)
                    # docker build -t myapp:latest .
                    # docker push myapp:latest
                    
                    echo "Simulating deployment..."
                    sleep 2
                    echo "✅ Application packaged and ready!"
                '''
            }
        }
    }
    
    post {
        always {
            echo "═══════════════════════════════════════════"
            echo "📊 BUILD SUMMARY"
            echo "═══════════════════════════════════════════"
            echo "Build Result: ${currentBuild.result}"
            echo "Build Number: ${BUILD_NUMBER}"
            echo "Build Duration: ${currentBuild.durationString}"
            echo "Timestamp: $(date '+%Y-%m-%d %H:%M:%S')"
            echo "═══════════════════════════════════════════"
        }
        
        success {
            echo "✅ BUILD SUCCESSFUL!"
            echo "🎉 Your application built and tested successfully!"
        }
        
        failure {
            echo "❌ BUILD FAILED!"
            echo "⚠️ Check the console output above for details."
        }
        
        unstable {
            echo "⚠️ BUILD UNSTABLE!"
            echo "📋 Some tests may have failed."
        }
    }
}
