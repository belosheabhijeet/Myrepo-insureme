pipeline {
  agent any
  tools {
    maven 'M2_HOME'
        }
stages {
   stage('Git Checkout') {
      steps {
        git 'https://github.com/belosheabhijeet/Myrepo-insureme.git'
           }
       }   
   stage('Build Package') {
       steps {
         sh 'mvn package'
       }
  }
   stage('Publish HTML Reports') {
     steps {
       publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/Insureme-Project/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
           }
        }
   stage('Create docker image of app') {
      steps {
        sh 'docker build -t belosheabhijeet/insure-me-app:1.0 .'
            }
                               }
   stage('Push the images to dockerhub') {
     steps {
         withCredentials([usernamePassword(credentialsId: 'docker-hub1', passwordVariable: 'docker_password', usernameVariable: 'docker_user')]) {  
        sh 'docker login -u ${docker_user} -p ${docker_password}'
        }
        sh 'docker push belosheabhijeet/insure-me-app:1.0'
      }
   }
}
}
