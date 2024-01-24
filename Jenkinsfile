#!/usr/bin/env groovy

pipeline {

    agent none

    stages {
        stage('Build & Test'){
            agent {
                docker {
                    image 'node'
                    args '-u root'
                        }
            }
            stages {
                    stage('Build') {
                        steps {
                            echo 'Building...'
                            sh 'npm install'
                            echo 'Done...'
            
                        }
                    }
                    stage('Test') {
                        steps {
                            echo 'Testing...'
                            sh 'npm test'
                        }
                    }
            }
        }
        
        stage('Deploy') {
            agent {label 'Built-In Node'}
             steps {
                script {
                    sh 'cd /root/hello_hapi'
                    sh 'git pull'
                    // Or use Docker Compose or a deployment tool specific to your environment
                    // ...
                }
             }
         }
    }
}
