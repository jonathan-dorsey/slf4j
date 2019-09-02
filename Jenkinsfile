#!/bin/env groovy

pipeline {
  agent any

  options {
      timeout(time: 5, unit: 'MINUTES') 
  }

  stages {

    stage('Build') {
      steps {
        withMaven( 
          sh 'mvn -X -e clean install deploy'
        )
      }
    }
    
    stage('Sonar') {
      steps {
        echo 'Perform static code analysis!'
      }
    }

    stage('Prompt Release') {
      steps {
        input "Release project?" 
      }
    }

    stage('Release') {
      steps {
        sh 'mvn release'
      }
    }
  }
}
