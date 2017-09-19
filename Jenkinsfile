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
                input message: 'Please approve', submitter: 'admin'
                nexusArtifactUploader artifacts: [[artifactId: 'helloworld', classifier: 'debug', file: 'target/helloworld.war', type: 'war']], credentialsId: 'nexus', groupId: 'testgroup', nexusUrl: '54.224.88.35:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'helloworld', version: '2'

            }
        }
    }
}
