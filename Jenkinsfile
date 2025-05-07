pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6' // Match the name from Global Tool Configuration
    }

    stages {
        stage('Compile') {
            steps {
                echo 'Compiling the code...'
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Code Review') {
            steps {
                echo 'Running Checkstyle for code review...'
                sh 'mvn checkstyle:check'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check above logs for details.'
        }
    }
}
