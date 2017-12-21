String tagDb = "v1.0.2"
String tagBack = "v1.0.4"
String tagFront = "v1.0.2"

echo "La branche actuelle est ${env.BRANCH_NAME}."

parallel db: {
		stage('Déploiement db') {
			build "../cpt-front/${tagDb}"		
		}
    }, back: {
		stage('Déploiement back') {
			build job: '../cpt-back/master', parameters: [string(name: 'ENV', value: 'env.BRANCH_NAME')]
		}
    }, front: {
		stage('Déploiement Front') {
			build "../cpt-front/${tagFront}"
		}
    }
