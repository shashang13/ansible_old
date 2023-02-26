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
          echo "This is a feature branch"
          env
        '''
      }
    }

    stage ('PR') {
      steps {
        sh '''
          echo "This is PR"
          env
        '''
      }
    }

    stage ('Main Branch') {
      when { branch 'main' }
      steps {
        sh '''
          echo "This is a Main branch"
          env
        '''
      }
    }
  }
}