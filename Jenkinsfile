pipeline {
    agent any

    tools {
        maven 'Maven 3.6.3' 
        jdk 'JDK 11' 
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Shivaredd/mavne-build1.git', credentialsId: 'jenkin'
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
