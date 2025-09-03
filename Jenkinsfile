// pipeline {
//   agent any

//    tools {nodejs "node"}

//   stages {
//     stage ("build") {
//       steps {
//         echo "building my app..."
//          npm install
//       }
//     }
//     stage ("test") {
//        steps {
//         sh "pwd"
//           dir('client') {
//               sh "pwd"
//               sh 'npm install'
//               sh 'npm test'
//               }
//         echo "testing my app..."
//        }
//     }
//     stage ("deploy") {
//     steps {
//         echo "deploying my app..."
//        }
//     }
//   }

// }


pipeline {
    agent any

    tools {
        nodejs "node"   // Jenkins NodeJS installation (configured in Manage Jenkins > Global Tool Configuration)
    }

    stages {
        stage('Build') {
            steps {
                echo "📦 Installing root dependencies..."
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests from root (client/src is included by npm scripts)..."
                sh 'npm test'
            }
        }

        stage('Build Client') {
            steps {
                echo "🏗️ Building client app..."
                sh 'npm run build --prefix client'
                // The --prefix option tells npm to run the script inside client/
                // This assumes client/package.json has a "build" script (common for React/Vue apps)
            }
        }

        stage('Deploy') {
            when {
                branch 'main'   // only deploy from the main branch
            }
            steps {
                echo "🚀 Deploying application to AWS from branch: ${env.BRANCH_NAME}"
                // Example deployment steps:
                // sh 'aws s3 sync client/build/ s3://my-bucket-name'
                echo "✅ Deployment complete!"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished for branch: ${env.BRANCH_NAME}"
        }
    }
}
