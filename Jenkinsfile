environment {
	VERSION = VersionNumber([projectStartDate: '2017-05-12', skipFailedBuilds: true, versionNumberString: '${YEARS_SINCE_PROJECT_START, XX}.${BUILD_MONTH, XX}.${BUILDS_THIS_MONTH}', versionPrefix: 'v']);
}

stage 'Checkout'
	node('master') {
		deleteDir()
		checkout scm
	}

stage 'Build & Archive Apk'
	node('master') {
  	sh 'export ANDROID_SERIAL=192.168.56.101:5555 ; echo $VERSION > build.txt'
  	step([$class: 'ArtifactArchiver', artifacts: 'build.txt'])
	}

stage('Deploy approval'){
	input "Deploy to prod?"
}

stage 'Deploy'
	node('master') {
		  echo VERSION
    	echo "deploying"
    	sh 'echo  "$VERSION;"'
	}

