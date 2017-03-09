node {
    def published_branches = ['master', 'firefox','frbayart-branch-2']
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
        sh 'exit 0'
      }
      catch (exc) {
        echo 'ERROR ROBERT'
        slackSend channel: '#stream', color: 'good', message: 'Slack Message'
        step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: []]])    
        throw exc
      }
    }

  stage('Example') {
    for (int i = 0; i < published_branches.size(); ++i) {
      if (env.BRANCH_NAME == published_branches[i]) {
        echo "DEPLOY the ${published_branches[i]} branch"
      } else {
        echo 'I execute elsewhere'
      }
    }
  }

    stage('Deploy'){
      echo 'Deploy !'
    }
}
