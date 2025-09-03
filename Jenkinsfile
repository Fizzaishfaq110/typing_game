pipeline {
 
  agent any
 
  stages {
 
    stage('Checkout') {
 
      steps {
 
        git url: 'https://github.com/Fizzaishfaq110/typing_game.git', branch: 'main'
 
      }
 
    }
 
    stage('Build') {
 
      steps {
 
        echo 'Building...'
 
        // Example: sh 'mvn clean compile' or 'npm install'
 
      }
 
    }
 
    stage('Test') {
 
      steps {
 
        echo 'Running tests...'
 
        // Example: sh 'mvn test' or 'npm test'
 
      }
 
    }
 
    stage('Deploy') {
 
      steps {
 
        echo 'Deploying...'
 
        // Example: sh './deploy.sh'
 
      }
 
    }
 
  }
 
}
 
 