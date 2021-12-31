pipeline {
    agent {
        ecs {
            inheritFrom 'build-example'
        }
    }
    options {
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '10')) // number of builds to keep on master
        disableConcurrentBuilds() // do not allow 2 builds at the same time for a given job
        ansiColor('xterm')
        disableResume()
        timeout(time: 20, unit: 'MINUTES')
    }
    tools {
    maven 'maven 3.8.4'
    }
    stages {
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
                sh "date"
            }
        }
    }
}
