pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven 3.6.3' // Adjust the tool name as per your Jenkins configuration
        PATH = "${env.MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Shivaredd/mavne-build1.git'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Clean and build your Maven project
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run your Maven tests
                    sh 'mvn test'
                }
            }
        }
        
        stage('Package') {
            steps {
                script {
                    // Package your Maven project
                    sh 'mvn package'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy your Maven project (if applicable)
                    sh 'mvn deploy'
                }
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully'
        }
        failure {
            echo 'Build failed'
        }
    }
}
        failure {
            echo 'Build failed.'
        }
    }
}
