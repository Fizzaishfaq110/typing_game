pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo 'Installing dependencies...'
        sh 'npm install'   // Run npm install to get all packages
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        // sh 'npm test'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying application...'
        echo 'Deployment step - add your deploy commands here!'
      }
    }
  }
}

}