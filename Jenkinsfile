pipeline {
  agent {
    label 'Group1'
  }

  stages {
    stage ('Roboshop Dry Run') {
      steps {
        sh 'ansible-playbook roboshop-check.yml -e ansible_user=centos -e ansible_password=DevOps321 -e role_name=frontend'
      }
    }
  }
}