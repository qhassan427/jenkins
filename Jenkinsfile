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
                // Windows batch command
                bat 'echo mvn clean install (replace with actual build command)'
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests == true } // Conditional execution
            }
            steps {
                echo 'Running tests...'
                // Windows batch command
                bat 'echo mvn test (replace with actual test command)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Windows batch command
                bat 'echo Deploying to server'
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
