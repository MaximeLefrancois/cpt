String tagDb = "v1.0.3"
String tagBack = "v1.0.5"
String tagFront = "v1.0.3"
String environment = "horsprod"

echo "La branche actuelle est ${env.BRANCH_NAME}."

if (env.BRANCH_NAME == 'develop'){
	environment = "horsprod"
} else if (env.BRANCH_NAME == 'master'){
	environment = "prod"
}

parallel db: {
		stage('Déploiement db') {
			build "../cpt-front/${tagDb}", parameters: [string(name: 'ENV_DB', value: "${environment}")]		
		}
    }, back: {
		stage('Déploiement back') {
			build job: "../cpt-back/${tagBack}", parameters: [string(name: 'ENV_BACK', value: "${environment}")]
		}
    }, front: {
		stage('Déploiement Front') {
			build "../cpt-front/${tagFront}", parameters: [string(name: 'ENV_FRONT', value: "${environment}")]
		}
    }
