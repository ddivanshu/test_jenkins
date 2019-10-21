pipeline {
//      agent any{ docker { image 'maven:3.3.3' } }
agent any
 stages {

           stage('begin'){
           steps {
            sh 'echo "begining-----------------------------------"'
                }
           }

 			stage('checkout scm') {

 				steps {
 					git branch: 'master', url: "https://github.com/ddivanshu/test_jenkins.git"
 				}
 			}


 			stage('test') {
 				steps {

            sh 'echo "testing started-----------------------------------"'
 					sh 'mvn clean install -DskipTests=false | egrep -v "([INFO])"'
 				}
 			}

 			stage('build') {
 				steps {
 				            sh 'echo "build started-----------------------------------"'

 					sh 'mvn package -DskipTests=true'
 					sh 'mvn spring-boot:run'
//  					archiveArtifacts artifacts: params.distPath + pipelineParams.distId + '.jar', fingerprint: true
 				}
 			}
}
}