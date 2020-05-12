pipeline {
    agent any
    stages {
      stage('Build dokcer image'){
        steps{
          dir('app') {
              git url: 'https://github.com/dobromir-hristov/todo-app'
              sh 'mv ../Dockerfile .'
              sh 'docker build -t todo . > build.txt'
          }
        }
        post {
          always {
            archiveArtifacts artifacts: 'app/build.txt'
          }
        }
      }
      stage('lint stage'){
        steps{
          sh 'docker run --rm --name todo-lint todo lint'
        }
      }
      stage('unit test stage'){
        steps{
          sh 'docker run --rm --name todo-unit-testing todo test:unit'
        }
      }
      stage('E2E test stage'){
        steps{
          sh 'docker run --rm --name todo-E2E-testing todo test:e2e --headless'
        }
      }
    }
}