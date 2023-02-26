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
    stage ('Validate Code quality') {
      when { branch pattern: "Rob.*", comparator: "REGEXP"}
      steps {
        sh '''
          echo "Execute Ansible lint check "
        '''
      }
    }

    stage ('Sandbox Env Validation') {
      when { branch pattern: "PR.*", comparator: "REGEXP"}
      steps {
        sh '''
          ansible-playbook roboshop-check.yml -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e role_name=frontend -e ENV=sandbox
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