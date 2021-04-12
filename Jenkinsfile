pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        git(credentialsId: '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', url: 'https://github.com/Dienstfreude/DO280-apps/tree/master/', branch: 'hello-world-nginx', changelog: true, poll: true)
      }
    }

  }
}