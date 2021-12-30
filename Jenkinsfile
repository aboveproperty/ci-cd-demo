pipeline {
    agent {
        ecs {
            inheritFrom 'build-example'
        }
    }  
    stages {
        stage('Checkout'){
           checkout scm
        }
        stage('Build'){
            // def mvnHome = tool 'Maven 3.3.x'
            // env.JAVA_HOME = tool 'JDK 1.8'

            if (isUnix()) {
                sh "git status"
                sh "git log"
                sh "mvn -version"
                sh "mvn clean verify"
            } else {
                bat "${mvnHome}\\bin\\mvn -version"
                bat "${mvnHome}\\bin\\mvn -Prun-its clean verify"
            }
        }
        stage('Local installation') {
            if (isUnix()) {
                sh "mvn -DskipTests install"
            } else {
                bat "${mvnHome}\\bin\\mvn -DskipTests install"
            }
        }
    }
}
