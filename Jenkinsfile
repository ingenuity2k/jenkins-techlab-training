pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timeout(time: 10, unit: 'MINUTES')
        timestamps()  // Timestamper Plugin
        disableConcurrentBuilds()
    }
    tools {
        jdk 'jdk11'
        maven 'maven36'
    }
    stages {
        stage('Build') {
            steps {

                sh 'java -version'

                sh 'javac -version'

                sh 'mvn --version'
            }
        }
    }
}
pipeline {
    agent {
        docker {
            image 'ruby:2.7.1'
          }
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timeout(time: 10, unit: 'MINUTES')
        timestamps()  // Timestamper Plugin
        disableConcurrentBuilds()
    }
    stages {
        stage('Info') {
            steps {
                sh  """#!/bin/bash
                    ruby --version
                    bundle --version
                """
            }
        }
    }
}
