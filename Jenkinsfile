stage 'Checkout'
	node('master') {
		deleteDir()
		checkout scm
	}

stage 'Build & Archive Apk'
	node('master') {
  	sh 'export ANDROID_SERIAL=192.168.56.101:5555 ; echo $ANDROID_SERIAL > build.txt'
  	step([$class: 'ArtifactArchiver', artifacts: 'build.txt'])
	}

stage('Deploy approval'){
	input "Deploy to prod?"
}

stage 'Deploy to prod'
	node('master') {
    	echo "deploying"
	}
