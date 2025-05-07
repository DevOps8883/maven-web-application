pipeline {
    agent any

    stages {
        stage('Compile') {
            agent {
                docker { image 'maven:3.8.6-openjdk-11' }
            }
            steps {
                echo 'Compiling the code...'
                sh 'mvn compile'
            }
        }

        stage('Test') {
            agent {
                docker { image 'maven:3.8.6-openjdk-11' }
            }
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Code Review') {
            agent {
                docker { image 'maven:3.8.6-openjdk-11' }
            }
            steps {
                echo 'Running code review checks...'
                sh 'mvn checkstyle:check'
            }
        }

        stage('Package') {
            agent {
                docker { image 'maven:3.8.6-openjdk-11' }
            }
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
