#!/usr/bin/env groovy

pipeline {
  agent any
  stages {
    stage('Run Pylinting') {
      parallel {
        stage('Run Pylinting') {
          steps {
            
            echo "current build number: ${currentBuild.number}"
            echo "previous build number: ${currentBuild.previousBuild.getNumber()}"
            def causes = currentBuild.rawBuild.getCauses()
            echo "causes: ${causes}"
            def rebuildCause0 = currentBuild.rawBuild.getCause(com.sonyericsson.rebuild.RebuildCause)
            echo "rebuildCause0: ${rebuildCause0}"
            echo "rebuild up number: ${rebuildCause0.getUpstreamBuild()}"

            echo sh(returnStdout: true, script: 'env')
            echo 'Build No:[${env.BUILD_NUMBER}] | Run Pylinting'
          }
        }
        stage('Run Unit Test') {
          steps {
            echo 'Build No:[${env.BUILD_NUMBER}] | Run Unit Test'
          }
        }
      }
    }
    stage('Build Docker Image') {
      steps {
        echo 'Build No:[${env.BUILD_NUMBER}] | Build Docker Image And Push to Jfrog'
      }
    }
    stage('Deploy to SIT') {
      options {
        timeout(time: 30, unit: 'SECONDS')
      }
      steps {
        input(message: 'Do you want to continue deployment to SIT?', ok: 'Continue')
        echo 'Build No:[${env.BUILD_NUMBER}] | Deploy to SIT'
      }
    }
    stage('Deploy to Prod') {
      steps {
        input(message: 'Do you want to continue deployment to Prod?', ok: 'Continue')
        echo 'Build No:[${env.BUILD_NUMBER}] | Deploy to Prod'
      }
    }
  }
}
