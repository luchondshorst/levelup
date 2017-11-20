pipeline {
    agent any
    tools {
        maven 'M3'
        jdk 'jdk1.8.0'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sh 'mvn verify -Pintegrationtest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Validate') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                echo 'Gelukt'
            }
        }
    }
    post {
        failure {
            echo 'Build gaat fout'
        }
    }
}