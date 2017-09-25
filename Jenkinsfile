#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper


    

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/ligado/hello-world-servlet.git'
 
                sh "/opt/maven/apache-maven-3.5.0/bin/mvn clean install"
 
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
          
        stage('Deploy') {
            steps {
                mail bcc: '', body: 'Please go to ${env.BUILD_URL}."', cc: '', from: '', replyTo: '', subject: 'Job \'${env.JOB_NAME}\' (${env.BUILD_NUMBER}) is waiting for input', to: 'sweta.ghosh@nagarro.com
                nexusArtifactUploader artifacts: [[artifactId: 'helloworld', classifier: 'debug', file: 'target/helloworld.war', type: 'war']], credentialsId: 'nexus', groupId: 'testgroup', nexusUrl: '54.224.88.35:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'helloworld', version: '4'

            }
        }
    }
    }
