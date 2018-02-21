pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'if [ -e pre-build.sh ]; then ./pre-build.sh; fi'
        sh '''#!/bin/bash
set -e
conda build .
'''
        sh 'if [ -e post-build.sh ]; then ./post-build.sh; fi'
      }
    }
  }
}
