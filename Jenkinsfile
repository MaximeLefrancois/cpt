String tagDb = "v1.0.4"
String tagBack = "v1.0.6"
String tagFront = "v1.0.4"
String environment = "horsprod"

properties([
   parameters([
      string(defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?', name: 'ENV_PARENT'),
	  string(defaultValue: '', description: 'Identifiant compte AD', name: 'LOGIN_PARENT'),
	  password(defaultValue: '', description: 'Password compte AD', name: 'PWD_PARENT')
   ])
])

echo "La branche actuelle est ${env.BRANCH_NAME}."

parallel db: {
	stage('Déploiement db') {
		build job: "../cpt-db/${tagDb}", parameters: [string(name: 'ENV_DB', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: "${LOGIN_PARENT}"), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]
	}
}, back: {
	stage('Déploiement back') {
		build job: "../cpt-back/${tagBack}", parameters: [string(name: 'ENV_BACK', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: "${LOGIN_PARENT}"), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]
	}
}, front: {
	stage('Déploiement Front') {
		build job: "../cpt-front/${tagFront}", parameters: [string(name: 'ENV_FRONT', value: "${ENV_PARENT}"), string(name: 'LOGIN', value: 'LOGIN_PARENT'), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]
	}
}
