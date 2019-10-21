pipeline {
    agent { docker { image 'maven:3.3.3' } }
 stages {
 			stage('checkout scm') {

 				steps {
 					deleteDir()
 					git branch: pipelineParams.branch, credentialsId: 'conman-private-key', url: pipelineParams.scmUrl
 				}
 			}
 			stage('test') {
 				steps {
 					sh 'mvn clean test'
 					jacoco()
 				}
 			}

 			stage('build') {
 				steps {
 					sh 'mvn package -DskipTests=true'
 					archiveArtifacts artifacts: params.distPath + pipelineParams.distId + '.jar', fingerprint: true
 				}
 			}
}
}