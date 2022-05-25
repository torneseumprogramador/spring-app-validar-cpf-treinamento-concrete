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
        sh '''mvn package -Dmaven.test.skip
docker build -t didox/ilab-java-tdd .
docker push didox/ilab-java-tdd'''
      }
    }

    stage('Deploy k8s') {
      steps {
        sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i hosts ansible.yml -u ubuntu --private-key /var/lib/jenkins/chave-privada-aws.pem'
      }
    }

  }
}