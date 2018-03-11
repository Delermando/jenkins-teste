environment {
	TESTE = 'aa'
	VERSION = VersionNumber projectStartDate: '2017-01-01', versionNumberString: 'freya', versionPrefix: '2.0.', worstResultForIncrement: 'FAILURE'
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
		 echo "${TESTE}"
		 echo "${VERSION}"
     echo "deploying"
	}

