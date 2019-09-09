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
    def app = docker.build("quay.io/doerler/jenkins:casc-latest")
    docker.withRegistry('https://quay.io', 'quay.io') {
      app.push('casc-latest')
    }
  }
}
