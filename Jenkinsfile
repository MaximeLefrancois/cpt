String tagDb = "v1.0.0"
String tagBack = "v1.0.0"
String tagFront = "v1.0.0"

node {
   echo 'Hello World'
   
   milestone 1
   stage('Déploiement db') {
        sh "echo Déploiement db $tagDb"
        checkout scm: [$class: 'GitSCM',
        userRemoteConfigs: [[url: 'https://github.com/MaximeLefrancois/cpt/db.git']],
        branches: [[name: "refs/tags/${tagDb}"]]],
        changelog: false, poll: false
        sh "ls"
        sh "cat ./Jenkinsfile"
        load "./Jenkinsfile"
    }
    
    milestone 2
    stage('Déploiement cpt-back') {
        sh "echo Déploiement cpt-db $tagBack"
        checkout scm: [$class: 'GitSCM',
        userRemoteConfigs: [[url: 'https://github.com/MaximeLefrancois/cpt/back.git']],
        branches: [[name: "refs/tags/${tagBack}"]]],
        changelog: false, poll: false
        sh "ls"
        sh "cat ./Jenkinsfile"
        load "./Jenkinsfile"
    }
    
    milestone 3
    stage('Déploiement cpt-front') {
       sh "echo Déploiement cpt-front $tagFront"
	           sh "echo Déploiement cpt-db $tagBack"
        checkout scm: [$class: 'GitSCM',
        userRemoteConfigs: [[url: 'https://github.com/MaximeLefrancois/cpt/front.git']],
        branches: [[name: "refs/tags/${tagBack}"]]],
        changelog: false, poll: false
        sh "ls"
        sh "cat ./Jenkinsfile"
        load "./Jenkinsfile"
    }
}