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
}
}
