node {
   stage('Init variables') {
       env.JAVA_OPTS="-Djava.net.preferIPv4Stack=true"
   }
   stage('SCM') {
        checkout scm
   }
   stage('Discover') {
        sh "env"
   }
}
