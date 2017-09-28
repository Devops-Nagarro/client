#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper
import hudson.model.*




pipeline {
    agent any
    stages {
        stage('Poll SCM') {
            steps {
                git 'https://github.com/ligado/hello-world-servlet.git'
            }
        }
        stage('Build') {
            steps {
            sh "/opt/maven/apache-maven-3.5.0/bin/mvn clean install"
            }
        }
        stage('Code analysis') {
			 steps {
				parallel (
					static: { sh "echo Static code analysis; sleep 5s; echo  Static code analysis completed" },
					dynamic: { sh "echo Dynamic code analysis; sleep 10s; echo Dynamic code analysis completed" }
				)
				}
				post {
					success {
					echo "Both analysis completed successfully. Moving to next stage."
					}
				}
	   
        }
        stage('Performace Testing') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                mail to: 'vinay.thakur@nagarro.com', subject: "Job name: ${env.JOB_NAME}" , body: "Please approve \n Job url: ${env.JOB_URL}"
                input message: 'Please approve', submitter: 'vinay'
                nexusArtifactUploader artifacts: [[artifactId: 'helloworld', classifier: 'debug', file: 'target/helloworld.war', type: 'war']], credentialsId: 'nexus', groupId: 'testgroup', nexusUrl: '34.203.241.217:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'helloworld', version: '4'

            }
        }
    }
}
