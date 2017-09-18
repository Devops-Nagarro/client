pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
stage 'approve build'
input 'Do you approve deployment?'
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
