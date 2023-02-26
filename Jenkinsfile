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
          echo -e "\e[35mThis is a feature branch\e[0m"
          env
        '''
      }
    }

    stage ('PR') {
      steps {
        sh '''
          echo -e "\e[35mThis is PR\e[0m"
          env
        '''
      }
    }

    stage ('Main Branch') {
      when { branch 'main' }
      steps {
        sh '''
          echo -e "\e[35mThis is a Main branch\e[0m"
          env
        '''
      }
    }
  }
}