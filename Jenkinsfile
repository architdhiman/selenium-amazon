pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Example: If you use Maven, ensure dependencies are resolved
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo 'Executing Selenium tests...'
                // Run your Selenium tests using Maven or any other test framework
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying test reports...'
                // Example: Archive or move reports to a deployment server
                archiveArtifacts artifacts: '**/target/*.html', allowEmptyArchive: true
                publishHTML([
                    reportDir: 'target/surefire-reports',
                    reportFiles: 'index.html',
                    reportName: 'Test Results'
                ])
            }
        }
        stage('Cleanup') {
            steps {
                echo 'Cleaning up workspace...'
                // Remove temporary files or unnecessary resources
                deleteDir() // Deletes the workspace to ensure a clean state
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
