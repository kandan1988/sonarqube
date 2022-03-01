pipeline {
    agent any

    stages {
        stage('SCM Code Checkout') {
            steps {
               // sh 'git clone http://192.168.56.118:7990/scm/dt/sonarscan.git'
              checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'admin', url: 'http://192.168.56.118:7990/scm/dt/sonarscan.git']]])
            }
        }
        stage('Sonar scan') {
            steps {
              script{
              def scannerHome = tool 'scanner'
              withSonarQubeEnv('Sonarqube') { // If you have configured more than one global server connection, you can specify its name
              sh "${scannerHome}/bin/sonar-scanner"
              }
                }
            }
        }
      	
        stage('Deploy') {
            steps {
                echo " to deploy"
              	
            }
        }
    }
}
