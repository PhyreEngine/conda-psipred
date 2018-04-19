pipeline {
  agent { label 'conda-build' }
  environment {
    tmpdir = "${pwd tmp: true}"
  }
  stages {
    stage('build') {
      steps {
        lock('conda-index') {
            sh './build'
        }
      }
      post {
        failure {
          withCredentials([string(credentialsId: 'email-recipients', variable: 'EMAIL_RECIPIENTS')]) {
            emailext (
                attachLog: true,
                to: "${EMAIL_RECIPIENTS}",
                subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed.
Check console output at ${env.BUILD_URL}."""
            )
          }
        }
      }
    }
  }
}
