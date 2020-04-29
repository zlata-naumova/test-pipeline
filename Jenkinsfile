pipeline {
  agent {
    docker {
      image 'cypress/base:10'
    }

  }
  stages {
    stage('build') {
      steps {
        echo "Running build ${env.BUILD_ID} on ${env.JENKINS_URL}"
        sh 'npm ci'
        sh 'cypress verify'
      }
    }

    stage('cypress parallel tests') {
      environment {
        CYPRESS_trashAssetsBeforeRuns = 'false'
      }
      parallel {
        stage('tester A') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'cypress run --record --parallel'
          }
        }

        stage('tester B') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'npm cypress run --record --parallel'
          }
        }

      }
    }

  }
}