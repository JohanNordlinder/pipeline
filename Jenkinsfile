pipeline {
  agent any
  stages {
    stage('Deploy TST') {
      steps {
        openshiftTag(srcStream: 'testarapp/app', srcTag: 'latest', destStream: 'testarapp/app-test', destTag: 'latest')
      }
    }
    stage('Deploy VER') {
      steps {
        input 'Deploy to VER?'
        openshiftTag(srcStream: 'testarapp/app-test', srcTag: 'latest', destStream: 'testarapp/app-ver', destTag: 'latest')
      }
    }
    stage('Deploy PRD') {
      steps {
        input 'Deploy to PRD?'
        openshiftTag(srcStream: 'testarapp/app-ver', srcTag: 'latest', destStream: 'testarapp/app-prod', destTag: 'latest')
      }
    }
  }
}