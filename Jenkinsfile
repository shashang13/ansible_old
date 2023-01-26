pipeline {
  agent {
    label 'Group1'
  }

  stages {
    stage ('Roboshop Dry Run') {
      steps {
        sh '''
          ansible-playbook -i inv roboshop.yaml -e HOST=FRONTEND -e role_name=frontend -C
        '''
      }
    }
  }
}