pipeline {
    agent {
        ecs {
            inheritFrom 'build-example'
        }
    }
    tools {
    maven 'maven 3.8.4'
  }
    stages{
        stage('Checkout'){
           steps{
                checkout scm
            }
        }
        stage('Build'){
            steps{
                sh "mvn --no-transfer-progress clean verify"
            }
        }
        stage('Local installation') {
            steps{
                sh "mvn -DskipTests --no-transfer-progress install"
            }
        }
    }
}
