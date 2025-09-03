pipeline {
  agent any

   tools {nodejs "node"}

  stages {
    stage ("build") {
      steps {
        echo "building my app..."
         npm install
      }
    }
    stage ("test") {
       steps {
        sh "pwd"
          dir('client') {
              sh "pwd"
              sh 'npm install'
              sh 'npm test'
              }
        echo "testing my app..."
       }
    }
    stage ("deploy") {
    steps {
        echo "deploying my app..."
       }
    }
  }

}