pipeline {
  agent {
    docker {
      image 'cypress/base:10'
    //   caching
    //   args '-v $HOME/.m2:/root/.m2'
    // args '-v $HOME/.cach:/root/.cash'
    // args '-v $HOME/.npm:/root/.npm'
    args '-v $PWD:/e2e'
    args '-w /e2e'
    // args '-v /tmp/.X11-unix:/tmp/.X11-unix '
    // args '-e $IP:0'
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

    }

    stage('cypress parallel tests') {
        environment {
        CYPRESS_trashAssetsBeforeRuns = 'false'
      }
    // }

    // stage('tester A') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh '$(npm bin)/cypress run'
          }
        }
  }
}

    // stage('cypress parallel tests') {
    //   environment {
    //     CYPRESS_trashAssetsBeforeRuns = 'false'
    //   }
    //   parallel {
    //     stage('tester A') {
    //       steps {
    //         echo "Running build ${env.BUILD_ID}"
    //         sh '$(npm bin)/cypress run -headless -b chrome --record --key=\'475a6393-b6e3-4065-86d1-b118626b5370\' --parallel'
    //       }
    //     }

    //     stage('tester B') {
    //       steps {
    //         echo "Running build ${env.BUILD_ID}"
    //         sh '$(npm bin)/cypress run --record --key=\'475a6393-b6e3-4065-86d1-b118626b5370\' --parallel'
    //       }
    //     }

    //   }
    // }

//   }
// }