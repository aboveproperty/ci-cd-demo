def mvnHome = tool 'maven 3.8.4'

pipeline {
    agent {
        ecs {
            inheritFrom 'build-example'
        }
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
                sh "${mvnHome}/bin/mvn -version"
                sh "${mvnHome}/bin/mvn clean verify"
            }
        }
        stage('Local installation') {
            steps{
                sh "${mvnHome}/bin/mvn -DskipTests install"
            }
        }
    }
}
