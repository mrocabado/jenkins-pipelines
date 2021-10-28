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
	echo "*** currentBuild.changeSets.size() : ${changeSets.size()} ***"
	
	def totalCountOfChanges = 0
	for (int i = 0; i < changeLogSets.size(); i++) {
		echo "*** changeSet #${i} has &{changeSets[i].items.length} changes/commits"
        totalCountOfChanges += changeSets[i].items.length
    }
	
	echo "*** Total number of changes ${totalCountOfChanges}"
}