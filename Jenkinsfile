pipeline {
    agent any
    tools {
        maven 'MAVEN' // Ensure this matches the Maven tool name configured in Jenkins
        jdk 'JDK' // Ensure this matches the JDK tool name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git branch: 'main', url: 'https://github.com/Shivaredd/mavne-build1.git' // Update branch name if needed
            }
        }

        stage('Initialize') {
            steps {
                echo "PATH = ${env.M2_HOME}/bin:${env.PATH}"
                echo "M2_HOME = ${env.M2_HOME}"
            }
        }

        stage('Build') {
            steps {
                dir('/var/lib/jenkins/workspace/demopipelinetask/my-app') {
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }
    }
    post {
        always {
            junit(
                allowEmptyResults: true,
                testResults: '**/test-reports/*.xml' // Adjust the path if needed
            )
        }
    }
}
