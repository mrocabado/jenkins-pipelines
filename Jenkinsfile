node {
    stage('Checkout') {
        echo 'Checkout....'
		//git credentialsId: 'git-ssh', branch: 'main', url: 'git@github.com:mrocabado/jenkins-pipelines.git'
		commitCount = getCommitCount()
		datadog(collectLogs: false, tags: ["commit_count:${commitCount}"]){
			echo 'Attaching commit_count tag....'
		}
    }
    stage('Build') {
        echo 'Building....'
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('Do nothing') {
 
    }
    stage('Deploy') {
        echo 'Deploying....'
    }	
}


@NonCPS
def getCommitCount() {
    def changeSets = currentBuild.changeSets
	echo "*** currentBuild.changeSets.size() : ${changeSets.size()} ***"
	
	def commitCount = 0
	for (int i = 0; i < changeSets.size(); i++) {
		echo "*** changeSet #${i} of kind '${changeSets[i].kind}' has ${changeSets[i].items.length} changes/commits"
        commitCount += changeSets[i].items.length
    }
	
	echo "*** Total number of changes ${commitCount}"
	return commitCount
}