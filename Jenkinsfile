pipeline {
  agent {
    label 'Group1'
  }
  options {
    ansiColor('xterm')
  }
  environment {
    SSH = credentials ('SSH')
  }


  stages {
    stage ('Feature branch') {
      steps {
        sh '''
          #ansible-playbook roboshop-check.yml -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e role_name=frontend -e ENV=sandbox
          env
          echo "This is a feature branch"
        '''
      }
    }

    stage ('PR') {
      steps {
        sh '''
          env
          echo "This is a PR"
        '''
      }
    }

    stage ('Main Branch') {
      steps {
        sh '''
          env
          echo "This is a Main branch"
        '''
      }
    }
  }
}