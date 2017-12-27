String tagDb = "v1.0.5"
String tagBack = "v1.0.7"
String tagFront = "v1.0.5"

echo "La branche actuelle est ${env.BRANCH_NAME}."

properties([
   parameters([
      string(defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?', name: 'ENV_PARENT'),
	  string(defaultValue: '', description: 'Identifiant compte AD', name: 'LOGIN'),
	  password(defaultValue: '', description: 'Password compte AD', name: 'PWD')
   ])
])

parallel db: {
	stage('Déploiement db') {
		build job: "../cpt-db/${tagDb}", parameters: [string(name: 'ENV_DB', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: "${LOGIN}"), password(description: 'Password compte AD', name: 'PWD', value: "${PWD}")]
	}
}, back: {
	stage('Déploiement back') {
		build job: "../cpt-back/${tagBack}", parameters: [string(name: 'ENV_BACK', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: "${LOGIN}"), password(description: 'Password compte AD', name: 'PWD', value: "${PWD}")]
	}
}, front: {
	stage('Déploiement Front') {
		build job: "../cpt-front/${tagFront}", parameters: [string(name: 'ENV_FRONT', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: 'LOGIN'), password(description: 'Password compte AD', name: 'PWD', value: "${PWD}")]
	}
}
