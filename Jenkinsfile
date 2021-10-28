node {
    stage('Checkout') {
        echo 'Checkout....'
		getChangeCount()
    }
    stage('Build') {
        echo 'Building....'
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}


@NonCPS
def getChangeCount() {
    def changeSets = currentBuild.changeSets
	echo "currentBuild.changeSets.size() :\n${changeSets.size()}"
}