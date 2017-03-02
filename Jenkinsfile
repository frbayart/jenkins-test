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
      try {
        sh "env"
        sh 'exit 1'
      }
      catch (exc) {
        echo 'ERROR ROBERT'
        slackSend channel: '#stream', color: 'good', message: 'Slack Message', teamDomain: 'beedemo', token: 'token'
        step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: []]])    
        throw exc
      }
    }

    stage('Deploy'){
      echo 'Deploy !'
    }
}
