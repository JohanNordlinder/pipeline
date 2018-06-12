pipeline {
  agent any
  stages {
    stage('Deploy TST') {
      steps {
        openshiftTag(srcStream: 'docker-registry.default.svc:5000/testarapp/app', srcTag: 'latest', destStream: 'docker-registry.default.svc:5000/testarapp/app-test', destTag: 'latest')
      }
    }
    stage('Deploy VER') {
      steps {
        input 'Deploy to VER?'
        openshiftTag(srcStream: 'docker-registry.default.svc:5000/testarapp/app-test', srcTag: 'latest', destStream: 'docker-registry.default.svc:5000/testarapp/app-ver', destTag: 'latest')
      }
    }
    stage('Deploy PRD') {
      steps {
        input 'Deploy to PRD?'
        openshiftTag(srcStream: 'docker-registry.default.svc:5000/testarapp/app-ver', srcTag: 'latest', destStream: 'docker-registry.default.svc:5000/testarapp/app-prod', destTag: 'latest')
      }
    }
  }
}