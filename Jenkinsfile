node {
    stage('Checkout') {
        echo 'Checkout....'
		git credentialsId: 'git-ssh', branch: 'main', url: 'git@github.com:mrocabado/jenkins-pipelines.git'
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