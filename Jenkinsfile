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
        sh '$(npm bin)/cypress verify'
      }
    }

    stage('cypress parallel tests') {
      environment {
        // CYPRESS_RECORD_KEY = credentials('cypress-example-kitchensink-record-key')
        CYPRESS_trashAssetsBeforeRuns = 'false'
      }
      parallel {
        stage('tester A') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh '$(npm bin)/cypress run'
            // --record --parallel'
          }
        }

        // stage('tester B') {
        //   steps {
        //     echo "Running build ${env.BUILD_ID}"
        //     sh '$(npm bin)/cypress run --record --parallel'
        //   }
        // }

      }
    }

  }
}