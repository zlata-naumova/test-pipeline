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
        sh 'npm run cy:verify'
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
            sh '$(npm bin)/cypress run --record --key=\'475a6393-b6e3-4065-86d1-b118626b5370\' --parallel'
          }
        }

        stage('tester B') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh '$(npm bin)/cypress run --record --key=\'475a6393-b6e3-4065-86d1-b118626b5370\' --parallel'
          }
        }

      }
    }

  }
}