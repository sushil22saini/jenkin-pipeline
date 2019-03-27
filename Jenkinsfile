pipeline {
  agent any
  stages {
    stage('Run Pylinting') {
      parallel {
        stage('Run Pylinting') {
          steps {
            echo 'Run Pylinting'
          }
        }
        stage('Run Unit Test') {
          steps {
            echo 'Run Unit Test'
          }
        }
      }
    }
    stage('Build Docker Image') {
      steps {
        echo 'Build Docker Image And Push to Jfrog'
      }
    }
    stage('Deploy to SIT') {
      steps {
        echo 'Deploy to SIT'
      }
    }
    stage('Deploy to Prod') {
      steps {
        echo 'Deploy to Prod'
      }
    }
  }
}