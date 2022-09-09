pipeline {
  agent {
    node {
      label 'go'
    }
  }
  parameters{
     string(name:'TAG_NAME',defaultValue: '',description:'')
  }
  environment {
    DOCKER_REPO_CREDENTIAL_ID = 'docker-repo-id'
    GIT_CREDENTIAL_ID = 'git-id'
    KUBECONFIG_CREDENTIAL_ID = 'demo-kubeconfig'
    DOCKER_REPO_NAMESPACE = 'kubesphere'
    GIT_ACCOUNT = 'kubesphere'
    APP_NAME = 'devops-go-sample'
    DOCKER_REPO_ADDRESS = 'harbor.devops.kubesphere.local:30280'
    GIT_ADDRESS = 'gitlab.devops.kubesphere.local:30080'
  }
  stages {
    stage('checkout scm') {
      steps {
        checkout(scm)
      }
    }

    stage('build') {
      steps {
        container('go') {
          sh 'go build -o main .'
        }
      }
    }
  }
}
