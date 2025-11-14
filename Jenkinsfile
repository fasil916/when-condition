pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Jenkins automatically detects the branch in a multibranch pipeline
                    checkout scm

                    // Output the branch name to confirm which branch is checked out
                    echo "Checked out branch: ${env.BRANCH_NAME}"
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building the application... Branch: ${env.BRANCH_NAME}"
                sh 'echo Build step running'
                // Add your build commands here
            }
        }

        stage('Push Image') {
            steps {
                echo "Pushing Docker image..."
                sh 'echo Image push running'
                // Replace with your Docker push commands
            }
        }

        // Deploy to DEV environment if branch is 'dev'
        stage('Deploy to Dev') {
            when {
                branch 'dev'  // Only runs when the branch is 'dev'
            }
            steps {
                echo "Deploying to DEV environment..."
                sh '''
                # Add your DEV deployment commands here
                echo "Deploying to DEV"
                '''
            }
        }

        // Deploy to PROD environment if branch is 'main'
        stage('Deploy to Prod') {
            when {
                branch 'main'  // Only runs when the branch is 'main'
            }
            steps {
                echo "Deploying to PROD environment..."
                sh '''
                # Add your PROD deployment commands here
                echo "Deploying to PROD"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline Succeeded ✅"
        }
        failure {
            echo "Pipeline Failed ❌"
        }
        always {
            echo "Pipeline Finished."
        }
    }
}
