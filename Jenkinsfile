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
    agent {
        docker {
            image 'node:20-bullseye'   // Node.js + Python + build tools included
            args '-u root'             // run as root so npm can install dependencies
        }
    }

    environment {
        NODE_OPTIONS = "--max-old-space-size=4096"  // optional, increase Node memory if needed
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
            }
        }

        stage('Deploy') {
            when {
                branch 'main'   // only deploy from main branch
            }
            steps {
                echo "🚀 Deploying application to AWS from branch: ${env.BRANCH_NAME}"
                // Example deployment commands:
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
