withCredentials([string(credentialsId: 'github-webhook-token', variable: 'githubWebhookToken')]) {
  properties([
    pipelineTriggers([GenericTrigger(causeString: 'Generic Cause', regexpFilterExpression: '', regexpFilterText: '', token: "jenkins_docker-${githubWebhookToken}")])
  ])
}

node(){
  stage('checkout'){
    checkout scm
  }
  stage('build'){
    def app = docker.image("quay.io/doerler/jenkins:casc_latest")
    docker.withRegistry('https://quay.io', 'quay.io') {
      app.push('casc_latest')
    }
  }
}
