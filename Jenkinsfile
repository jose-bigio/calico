#!groovy

stage(name: 'calico-integration-test') {
	wrappedNode(label: 'aufs', cleanWorkspace: true) {
		checkout scm

		sh("make -C calico_node semaphore")
	}
}
