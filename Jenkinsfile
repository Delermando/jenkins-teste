environment {
  VERSION = VersionNumber([
    versionNumberString : '${BUILD_YEAR}.${BUILD_MONTH}.${BUILD_ID}',
    projectStartDate : '2014-05-19'
  ]);
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
    	echo "deploying"
	}

