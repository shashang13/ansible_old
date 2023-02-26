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