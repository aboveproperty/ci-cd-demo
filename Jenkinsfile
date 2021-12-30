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
            // def mvnHome = tool 'Maven 3.3.x'
            // env.JAVA_HOME = tool 'JDK 1.8'
            steps{
                sh "git status"
                sh "git log"
                sh "mvn -version"
                sh "mvn clean verify"
            }
        }
        stage('Local installation') {
            steps{
                sh "mvn -DskipTests install"
            }
        }
    }
}
