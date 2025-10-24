pipeline {
    agent any  // Jenkins can use any available agent or node

    environment {
        // You can define environment variables here if needed
        APP_ENV = "dev"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out the repository..."
                checkout scm  // pulls the latest code from GitHub
            }
        }

        stage('Build') {
            steps {
                echo "Building the application..."
                // Example: build commands (customize these for your project)
                sh 'echo Building project...'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Example: run tests (replace with your own commands)
                sh 'echo Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // Example deployment command (replace with real one)
                sh 'echo Deploying to environment...'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed! Check logs for details."
        }
        always {
            echo "Pipeline finished execution."
        }
    }
}
