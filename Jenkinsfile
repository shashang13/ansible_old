pipeline {
  agent {
    label 'Group1'
  }

  stages {
    stage ('Roboshop Dry Run') {
      steps {
        sh '''
          ansible-playbook -i localhost, roboshop.yaml -e role_name=frontend
        '''
      }
    }
  }
}