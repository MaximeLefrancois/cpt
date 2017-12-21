String tagDb = "v1.0.2"
String tagBack = "v1.0.4"
String tagFront = "v1.0.2"
String env = "horsprod"

echo "La branche actuelle est ${env.BRANCH_NAME}."

if (env.BRANCH_NAME == 'develop'){
	env = "horsprod"
} else if (env.BRANCH_NAME == 'master'){
	env = "prod"
}

parallel db: {
		stage('Déploiement db') {
			build "../cpt-front/${tagDb}", parameters: [string(name: 'ENV', value: "${env}")]		
		}
    }, back: {
		stage('Déploiement back') {
			build job: "../cpt-back/${tagBack}", parameters: [string(name: 'ENV', value: "${env}")]
		}
    }, front: {
		stage('Déploiement Front') {
			build "../cpt-front/${tagFront}", parameters: [string(name: 'ENV', value: "${env}")]
		}
    }
