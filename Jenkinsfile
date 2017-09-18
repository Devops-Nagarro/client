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
        stage('Deploy') {
	input 'Do you approve deployment?'
            steps {
                echo 'Deploying....'
            }
        }
    }
}
