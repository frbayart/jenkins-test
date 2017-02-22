pipeline {
    agent any 
   stages {
   stage('Init variables') {
       env.JAVA_OPTS="-Djava.net.preferIPv4Stack=true"
   }
   stage('SCM') {
      steps {
         timeout(time: 2, unit: 'MINUTES') {
         retry(3) {
        checkout scm
         }
         }
         step([$class: 'GitHubSetCommitStatusBuilder'])
      }

   }
   stage('Discover') {
        sh "env"
   }
      stage('Deploy'){
         success {
            echo 'This will run only if successful'
         }
         failure {
            echo 'This will run only if failed'
         }
      }
   }}
