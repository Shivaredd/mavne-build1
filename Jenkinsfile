pipeline {
    agent any
    tools {
        maven 'MAVEN'
        jdk 'JDK'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Shivaredd/mavne-build1.git'
            }
        }

        stage('Initialize') {
            steps {
                echo "M2_HOME = ${env.M2_HOME}"
                echo "PATH = ${env.PATH}"
            }
        }

        stage('Build') {
            steps {
                dir('/var/lib/jenkins/workspace/demopipelinetask/my-app') {
                    sh 'mvn -B compile'
                    sh 'mvn -B test'
                    sh 'mvn -B package'
                    sh 'mvn -B install'
                }
            }
        }
    }
    post {
        always {
            junit(
                allowEmptyResults: true,
                testResults: '**/test-reports/*.xml'
            )
        }
    }
}
