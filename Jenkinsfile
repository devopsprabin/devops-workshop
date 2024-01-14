pipeline {
  agent any
  stages {
    stage('Start'){
      steps {
        echo "Pipeline Started && Login successfully "
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t workshop:latest .'
      }
    }
    stage('Docker Push') {
      steps {
          sh "docker login -u devopsprabin -p '%41ry&i*bs#5P7NU12'"
          sh 'docker push workshop:latest'
        }
      }
    stage('Clean docker image') {
      steps {
        sh 'docker rmi workshop:latest'
      }
    }
    stage('deployed to Ubuntu server ') {
      steps{
          sh 'ssh  -o StrictHostKeyChecking=no  root@$192.168.100.112 "cd /home/workshop && docker-compose up -d"'
        }
      }
    }
  }

