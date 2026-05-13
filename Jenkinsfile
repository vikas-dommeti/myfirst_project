// // pipeline {
// //     agent any

// //     stages {

// //         stage('Git Pull') {
// //             steps {
// //                 echo 'Pulling Code'
// //             }
// //         }

// //         stage('Build') {
// //             steps {
// //                 sh 'echo Build Started'
// //             }
// //         }

// //         stage('Test') {
// //             steps {
// //                 sh 'echo Testing'
// //             }
// //         }

        
// //     }
// // }


// pipeline {
//     agent any

//     stages {

//         stage('Clone Repository') {
//             steps {
//                 echo "Repository cloned"
//             }
//         }

//         stage('List Files') {
//             steps {
//                 sh 'ls -lrt'
//             }
//         }

//         stage('Test All Files') {
//             steps {
//                 sh '''
//                 echo "Starting file testing..."

//                 for file in *.md
//                 do
//                     echo "========================="
//                     echo "Testing File: $file"
//                     echo "========================="

//                     if [ -f "$file" ]; then
//                         echo "$file exists"
//                         cat "$file"
//                         echo "$file tested successfully"
//                     else
//                         echo "$file not found"
//                         exit 1
//                     fi
//                 done
//                 '''
//             }
//         }
//     }

//     post {
//         success {
//             echo 'All files tested successfully'
//         }

//         failure {
//             echo 'Some file testing failed'
//         }
//     }
// }



pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package Application') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t vikasdommeti/java-app:v1 .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push vikasdommeti/java-app:v1'
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Tests failed or build failed'
        }
    }
}