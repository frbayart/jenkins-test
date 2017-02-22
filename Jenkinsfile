node {
    stage('Init variables') {
        env.JAVA_OPTS="-Djava.net.preferIPv4Stack=true"
    }
    stage('SCM') {
        timeout(time: 2, unit: 'MINUTES') {
          retry(3) {
           checkout scm
          }
        }
        step([$class: 'GitHubSetCommitStatusBuilder'])
    }

    stage('Discover') {
        sh "env"
    }

    stage('Deploy'){
          echo 'Deploy !'
    }
}
