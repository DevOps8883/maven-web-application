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
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Code Review') {
            steps {
                echo 'Running static code analysis...'
                sh 'mvn checkstyle:checkstyle'  // You can use SonarQube or other tools here
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
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
