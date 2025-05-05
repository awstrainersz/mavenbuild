pipeline {
    agent any
    tools {
        maven "mymaven"  // Name matches Jenkins' Global Tool Config
        
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/awstrainersz/mavenbuild.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'  // Publish test results
                }
            }
        }
    }
}
