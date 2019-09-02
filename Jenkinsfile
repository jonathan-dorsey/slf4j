#!/bin/env groovy

pipeline {
  options {
      timeout(time: 5, unit: 'MINUTES') 
  }

  properties(
    [
      pipelineTriggers(
        [ 
          githubPush()
        ]
      )
    ]
  )

  stages {

    stage('Build') {
      steps {
        sh 'mvn -X -e clean install deploy'
      }
    }
    
    stage('Sonar') {
      steps {
        echo 'Perform static code analysis!'
      }
    }
  }
}
