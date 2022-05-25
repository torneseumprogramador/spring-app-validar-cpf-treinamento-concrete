pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn package -Dmaven.test.skip'
      }
    }

    stage('Teste Unidade') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Docker Push') {
      steps {
        sh '''docker build -t didox/ilab-java-tdd .
docker push didox/ilab-java-tdd'''
      }
    }

  }
}