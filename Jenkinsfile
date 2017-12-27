String tagDb = "v1.0.4"
String tagBack = "v1.0.6"
String tagFront = "v1.0.4"
String environment = "horsprod"

echo "La branche actuelle est ${env.BRANCH_NAME}."

properties([
   parameters([
      string(defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?', name: 'ENV'),
	  string(defaultValue: '', description: 'Identifiant compte AD', name: 'LOGIN'),
	  password(defaultValue: '', description: 'Password compte AD', name: 'PWD')
   ])
])

//if (env.BRANCH_NAME == 'develop'){
//	environment = "horsprod"
//} else if (env.BRANCH_NAME == 'master'){
//	environment = "prod"
//}

parallel db: {
		stage('Déploiement db') {
			build job: "../cpt-db/${tagDb}", parameters: [string(name: 'ENV_DB', value: "${ENV}"), string(name: 'LOGIN', value: "${LOGIN}"), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]

		}
    }, back: {
		stage('Déploiement back') {
			build job: "../cpt-back/${tagBack}", parameters: [string(name: 'ENV_BACK', value: "${ENV}"), string(name: 'LOGIN', value: "${LOGIN}"), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]
		}
    }, front: {
		stage('Déploiement Front') {
			build job: "../cpt-front/${tagFront}", parameters: [string(name: 'ENV_FRONT', value: "${ENV}"), string(name: 'LOGIN', value: 'Max'), password(description: 'Password compte AD', name: 'PWD', value: <object of type hudson.util.Secret>)]
		}
    }
