pipeline {
    agent none 
    stages {
        stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        sh 'npm i'
    }

    stage('Test') {
        sh 'npm test'
    }

    stage('Publish') {
        sh 'npm start'
    }
    }
}