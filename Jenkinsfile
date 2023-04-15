pipeline {
  agent any

  options {
    ansiColor('xterm')
  }
  environment {
    SSH = credentials('SSH')
  }

  stages {
    stage ('Feature branch') {
      when { branch pattern: "ROB-.*", comparator: "REGEXP" }
//      when {
//         not {branch 'main'}
//         not {branch pattern: "PR-.*", comparator: "REGEXP"}
//      }
      steps {
        sh 'env'
        sh 'echo Executed Ansible style check'
      }
    }

    stage ('PR') {
      when { branch pattern: "PR-.*", comparator: "REGEXP"}
      steps {
        sh 'ansible-playbook roboshop-check.yml -e role_name=frontend -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e ENV=sandbox'
        echo "PR Step"
      }
    }

    stage ('MAIN') {
      when { branch 'main'}
      steps{
        dir('code'){
          git branch: 'main', url: 'https://github.com/shashang13/ansible.git'
          sh '''
            C_Tag=$(git tag --format="%(creatordate:unix)%09%(refname:strip=2)"|sort -nr -k1|head -1|awk '{print $2}')
            i_num=$(git tag --format="%(creatordate:unix)%09%(refname:strip=2)"|sort -nr -k1|head -1|awk '{print $2}'|awk -F . {print $3})
            i_num=i_num+1
            N_Tag=$(cut -c -4 C_Tag)
            echo "${N_Tag} ${i_num}"
          '''
        }
      }
    }
  }
}