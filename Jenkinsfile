pipeline {
    agent any
    tools {
        maven "M399" // Use the correct Maven tool name configured in Jenkins
    }

    stages {
        stage('Echo Version') {
            steps {
                echo "Printing Maven version..."
                sh 'mvn -version'

                echo "Checking Java version..."
                sh 'java -version'
            }
        }
        stage('Build') {
            steps {
                // echo "Cloning the Git repository..."
                // git branch: 'main', url: 'https://github.com/sankabha/jenkins-hello-world.git'

                // Run Maven Package CMD.
                echo "Building the project and skipping tests with Java version override..."
                sh "mvn clean package -DskipTests=true -X"
            }
        }
        stage('Unit Test') {
            steps {
                echo "Running Unit Tests with Java version override..."
                sh "mvn test -X"
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
