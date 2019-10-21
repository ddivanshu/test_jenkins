pipeline {
    agent { docker { image 'maven:3.3.3' } }
 stages {

           stage('begin'){
           steps {
            sh 'echo "begining-----------------------------------"'
                }
           }

 			stage('checkout scm') {

 				steps {
 					deleteDir()
 					git branch: 'master', url: "https://github.com/ddivanshu/test_jenkins.git"
 				}
 			}


 			stage('test') {
 				steps {

            sh 'echo "testing started-----------------------------------"'
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