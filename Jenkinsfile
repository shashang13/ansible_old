pipeline {
  agent {
    label 'Group1'
  }
  options {
    ansiColor('xterm')
  }
  environment {
    SSH = credentials (SSH)
  }

  stages {
    stage ('Roboshop Dry Run') {
      steps {
        sh '''
          ansible-playbook roboshop-check.yaml -e role_name=frontend -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e ENV=sandbox
        '''
      }
    }
  }
}