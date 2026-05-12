pipeline {
agent any

    stages {

        stage('Git Pull') {
            steps {
                echo 'Pulling Code'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Build Started'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Testing'
            }
        }


    }

}
