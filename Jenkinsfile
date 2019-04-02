pipeline {
  agent any
  stages {
    stage('Run Pylinting') {
      parallel {
        stage('Run Pylinting') {
          steps {
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
