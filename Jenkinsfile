pipeline {
    agent any

    stages {
        
         stage('Checkout') {
            steps {
                
                
               
                git branch: 'main', url: 'https://github.com/fasil916/when-condition.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the application...${env.BRANCH_NAME}"
                sh 'echo Build step running'
                // Replace with your real build commands
            }
        }

        stage('Push Image') {
            steps {
                echo "Pushing Docker image..."
                sh 'echo Image push running'
                // Replace with your docker push commands
            }
        }

        stage('Deploy to main') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying to main environment..."
                sh '''
                # Add your DEV deployment commands here
                echo "Deploying to DEV"
                '''
            }
        }

        stage('Deploy to PROD') {
            when {
                branch 'prod'
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
        success { echo "Pipeline Succeeded ✅" }
        failure { echo "Pipeline Failed ❌" }
        always { echo "Pipeline Finished." }
    }
}
