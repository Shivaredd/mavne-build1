pipeline {
    agent any

    tools {
        maven 'Maven 3.6.3' // Adjust to the Maven version installed on your Jenkins server
        jdk 'JDK 11' // Adjust to the JDK version installed on your Jenkins server
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://your-repository-url.git' // Replace with your repository URL
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '*/target/.jar', allowEmptyArchive: true
            junit 'target/surefire-reports/*.xml'
        }
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
