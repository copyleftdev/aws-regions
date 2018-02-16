pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'make install'
      }
    }
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'sonarqube'
          }
        }
        stage('coverage') {
          steps {
            sh 'unittest'
          }
        }
        stage('unit') {
          steps {
            sh 'coveralls'
          }
        }
      }
    }
    stage('canary') {
      steps {
        sh 'canary.sh'
      }
    }
    stage('deploy') {
      steps {
        sh 'deploy.sh'
      }
    }
  }
}