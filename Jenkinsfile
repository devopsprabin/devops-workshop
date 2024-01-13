pipeline {
  agent any
  stages {
    stage('Start'){
      steps {
        // sh "docker login -u devopsprabin -p aHHHHHHGGFFDFDDDDSDCVVVBNNMMMK "
        echo "Pipeline Started && Login successfully "
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -f Dockerfile -t workshop:latest  .'
      }
    }
    stage('Docker Push') {
      steps {
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
}