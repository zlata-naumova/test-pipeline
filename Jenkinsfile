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

<<<<<<< HEAD

=======
    stage('start local server') {
      steps {
        sh 'nohup npm run start:ci &'
      }
    }
>>>>>>> 7345c16518a3f2b03b9364b62e01299f1f73c188

    stage('cypress parallel tests') {
      environment {
        CYPRESS_trashAssetsBeforeRuns = 'false'
      }
      parallel {
        stage('tester A') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'npm run e2e:record:parallel'
          }
        }

        stage('tester B') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'npm run e2e:record:parallel'
          }
        }

      }
    }

<<<<<<< HEAD

=======
  }
  post {
    always {
      echo 'Stopping local server'
      sh 'pkill -f http-server'
    }

  }
>>>>>>> 7345c16518a3f2b03b9364b62e01299f1f73c188
}