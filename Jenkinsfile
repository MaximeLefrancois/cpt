String tagDb = "v1.0.0"
String tagBack = "v1.0.0"
String tagFront = "v1.0.0"

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