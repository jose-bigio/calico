#!/groovy

// steps
def genTestJob(int batchNumber) {
	return [ "test-${batchNumber}" : { ->
		wrappedNode(label: 'docker-edge&&ubuntu', cleanWorkspace: true) {
			checkout scm
			sh("sudo make -C calico_node ST_OPTIONS=\"-A batchnumber==${batchNumber}\" ci")
		}
	}]
}

testJobs = [:]
for ( i = 0; i < 6; i++) {
	testJobs << genTestJob(i)
}

stage("Testing") {
	parallel(testJobs)
}
