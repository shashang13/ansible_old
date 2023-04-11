pipeline {
  agent any

  options {
    ansiColor('xterm')
  }
  environment {
    SSH = credentials('SSH')
  }

  stages {
//     stage ('Feature branch') {
//       when { branch pattern: "ROB-.*", comparator: "REGEXP" }
// //      when {
// //         not {branch 'main'}
// //         not {branch pattern: "PR-.*", comparator: "REGEXP"}
// //      }
//       steps {
//         sh 'env'
//         sh 'echo Executed Ansible style check'
//       }
//     }
//
//     stage ('PR') {
//       when { branch pattern: "PR-.*", comparator: "REGEXP"}
//       steps {
//         sh 'ansible-playbook roboshop-check.yml -e role_name=frontend -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e ENV=sandbox'
//         echo "PR Step"
//       }
//     }

    stage ('Test') {
      sh '''
        env
      '''

    }

 }
}