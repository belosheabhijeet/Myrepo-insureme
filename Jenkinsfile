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
         sh 'maven package'
       }
  }
}
}
