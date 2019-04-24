pipeline {
    options {
        disableConcurrentBuilds()
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '30'))
    }
    agent any
    stages {
        stage('Show runtime version') {
            steps {
                sh 'java -version'
                sh './mvnw --version'
                sh 'printenv| sort'
            }
        }
        stage('mvn cleanup') {
            steps {
                sh './mvnw clean'
            }
        }
        stage('Unit Tests') {
            steps {
                sh './mvnw test'
            }
        }
        stage('package') {
            steps {
                sh './mvnw -DskipTests package'
            }
        }
        stage('artifact upload') {
            steps {
                echo 'dont upload that shit'
            }
        }
        stage('docker build') {
            steps {
                sh "docker build . -t cy4n/broken:${env.GIT_COMMIT}"
            }
        }
        stage('docker push') {
            steps {
                echo 'dont upload that shit'
            }
        }
    }
}
