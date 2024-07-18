pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven'  // Assuming you have a Maven tool configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/my-form-app.git'  // Replace with your repository URL
            }
        }

        stage('Build') {
            steps {
                script {
                    def mvnHome = tool name: 'Maven', type: 'hudson.tasks.Maven$MavenInstallation'
                    sh "${mvnHome}/bin/mvn clean package"
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/my-form-app-1.0-SNAPSHOT.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

