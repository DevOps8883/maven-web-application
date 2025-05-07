pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-11' // or another Maven+JDK version
            args '-v /root/.m2:/root/.m2'  // optional: caches Maven dependencies
        }
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
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Code Review') {
            steps {
                echo 'Running code quality checks...'
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
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
