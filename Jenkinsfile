pipeline {
  agent {
    label 'Group1'
  }
  options {
    ansiColor('xterm')
  }
  environment {
    SSH = credentials('SSH')
  }

  stages {
    stage ('Feature branch') {
      when { branch pattern: "ROB-.*", comparator: "REGEXP" }
      steps {
        sh 'env'
        sh 'echo This is a feature branch'
      }
    }

    stage ('PR') {
      when { branch pattern: "PR-.*", comparator: "REGEXP"}
      steps {
        sh 'env '
        sh 'echo This is a PR'
      }
    }

    stage ('Main Branch') {
      when { branch 'main' }
      steps {
        sh 'env'
        sh 'echo This is Main branch'
      }
    }
//     stage ('Roboshop Dry Run') {
//       steps {
//         sh '''
//           env
//           #ansible-playbook roboshop-check.yaml -e role_name=frontend -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e ENV=sandbox
//         '''
//       }
//     }
  }
}