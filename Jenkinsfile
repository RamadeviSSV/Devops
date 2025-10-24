pipeline {
    agent any

    environment {
        APP_ENV = "dev"
        EC2_USER = "ubuntu"                     // Replace with your EC2 username
        EC2_IP   = "13.60.211.189"          // Replace with your EC2 public IP
        SSH_KEY  = "sony-key.pem"       // Path to SSH private key accessible by Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out the repository..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building the application..."
                sh 'echo Building project...'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo Running tests...'
            }
        }

        stage('Deploy HTML') {
            steps {
                echo "Deploying HTML page to EC2 Nginx..."
                sh """
                    scp -i ${SSH_KEY} -o StrictHostKeyChecking=no trigger-jenkins-build.html ${EC2_USER}@${EC2_IP}:/var/www/html/index.html
                    ssh -i ${SSH_KEY} -o StrictHostKeyChecking=no ${EC2_USER}@${EC2_IP} 'sudo systemctl restart nginx'
                """
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed! Check logs."
        }
        always {
            echo "Pipeline finished execution."
        }
    }
}
