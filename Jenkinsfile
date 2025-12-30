pipeline {
    agent any

    // Define environment variables accessible by all stages
    environment {
        VERSION = '1.0.0'
    }  

    // Define parameters
    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the test stage?')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building project version: ${VERSION}"
                // For Windows use: bat 'mvn clean install'
                sh 'mvn clean install' 
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests == true } // Conditional execution
            }
            steps {
                echo 'Running tests...'
                // Example test command
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Example deploy command
                sh 'echo Deploying to server'
            }
        }
    }

    // Post-build actions
    post {
        always {
            echo 'Pipeline Completed (Always)'
        }
        success {
            echo 'Pipeline Succeeded!'
        }
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
