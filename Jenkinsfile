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
 					git branch: 'master', url: "https://github.com/ddivanshu/test_jenkins.git"
 				}
 			}


 			stage('test') {
 				steps {

            sh 'echo "testing started-----------------------------------"'
 					sh 'mvn install -DskipTests=false | egrep -v "(^\[INFO\])"'
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