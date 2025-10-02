pipeline {
    agent any

    triggers {
        // Auto-trigger build when GitHub webhook sends push/PR event
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // replace with your build command
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                // replace with your test command
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo "✅ Build passed"
        }
        failure {
            echo "❌ Build failed"
            error("Failing PR build")
        }
    }
}
