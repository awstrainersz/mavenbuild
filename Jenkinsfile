pipeline {
    agent any
    tools {
        maven 'mymaven' // Ensure this matches your Jenkins Maven installation name
     }
    environment {
        POM_PATH = 'pom.xml' // Set this to the relative path of your pom.xml
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/awstrainersz/mavenbuild.git', branch: 'master'
            }
        }
        stage('List Files (Debug)') {
            steps {
                sh 'ls -l'
                sh 'ls -l ' // List files in the subfolder for verification
            }
        }
        stage('Build') {
            steps {
                sh "mvn -f ${POM_PATH} clean package"
            }
        }
        stage('Test') {
            steps {
                sh "mvn -f ${POM_PATH} test"
            }
            post {
                always {
                    junit 'my-app/target/surefire-reports/*.xml' // Adjust if your reports are elsewhere
                }
            }
        }
    }
}
