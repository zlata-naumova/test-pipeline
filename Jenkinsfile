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
        sh '''pwd
cd /var/jenkins_home/workspace/test-pipeline2_master/cypress/integration/examples
ls'''
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
<<<<<<< HEAD
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
=======
            sh '$(npm bin)/cypress run --parallel'
          }
        }

        stage('tester B') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh '$(npm bin)/cypress run --parallel'
          }
        }
>>>>>>> a27f3e923ec68773b752355bb65721c181c4fa6a

      }
    }

  }
}