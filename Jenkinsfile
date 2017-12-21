String tagDb = "v1.0.1"
String tagBack = "v1.0.1"
String tagFront = "v1.0.1"

echo "La branche actuelle est ${env.BRANCH_NAME}."

parallel db: {
		stage('Déploiement db') {
			build "../cpt-db/${tagDb}"
		}
    }, back: {
		stage('Déploiement db') {
			build "../cpt-back/${tagBack}"
		}
    }, front: {
		stage('Déploiement db') {
			build "../cpt-front/${tagFront}"
		}
    }
