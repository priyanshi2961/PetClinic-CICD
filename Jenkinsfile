pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📦 Cloning the repository...'
                git branch: 'main', url: 'https://github.com/priyanshi2961/PetClinic-CICD.git'
            }
        }

        stage('Build') {
            steps {
                echo '🏗️ Building the project...'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '📦 Packaging application...'
                bat 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo '📁 Archiving build artifacts...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build Successful!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
