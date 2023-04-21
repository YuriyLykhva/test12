pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-1', url: 'https://github.com/YuriyLykhva/test12.git']])
            }
        }
        stage('Test') {
            steps {
                bat 'mvn clean test'
            }
        }
        stage('Allure') {
            steps {
                allure includeProperties: false, jdk: '', results: [[path: 'tests/target/allure-results']]
            }
        }
    }
}
// ***JENKINS_SERVER_URL***/job/***JENKINS_JOB_NAME***/build?token=***JENKINS_BUILD_TRIGGER_TOKEN***
// http://192.168.0.101:8090/job/test13/build?token=jenkins_token_123
// http://192.168.0.101:8090/job/test13/github-webhook/build?token=jenkins_token_123