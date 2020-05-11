pipeline {
    agent any
    stages {
      stage('Build dokcer image'){
        steps{
          dir('app') {
              git url: 'https://github.com/dobromir-hristov/todo-app'
              sh 'mv ../Dockerfile .'
              sh 'docker build -t todo .'
          }
        }
        
      }
      stage('lint stage'){
        steps{
          sh 'docker run --rm --name todo-lint todo lint'
        }
      }
    }
}