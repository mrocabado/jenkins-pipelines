import java.util.concurrent.ThreadLocalRandom

node {
    stage('Checkout') {
        echo 'Checkout....'
		//git credentialsId: 'git-ssh', branch: 'main', url: 'git@github.com:mrocabado/jenkins-pipelines.git'
		commitCount = getCommitCount()
		changeVolume = commitCount == 0 ? 'none' : (commitCount == 1 ? 'single' : 'multiple' )
		datadog(collectLogs: false, tags: ["commit_count:${commitCount}", "change_volume:${changeVolume}"]){
			echo 'Attaching commit_count tag....'
		}
    }
    stage('Build') {
        echo 'Building....'
    }
    stage('Test') {
		double rdn = ThreadLocalRandom.current().nextDouble()
		echo "Testing....random = ${rdn}"
		if ( rdn > 0.7 ) {
			echo "Failing Job"
			currentBuild.result = 'FAILURE'
		}
    }
    stage('Do nothing') {
		echo 'Waiting....'
		
        try {
            Thread.sleep(ThreadLocalRandom.current().nextInt(1000, 5000))
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();  //preserve the fact that this thread was interrupted
        }
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
