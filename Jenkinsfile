

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
  	sh 'export ANDROID_SERIAL=192.168.56.101:5555 ; echo "$VERSION $TESTE" > build.txt'
  	step([$class: 'ArtifactArchiver', artifacts: 'build.txt'])
	}


stage 'Deploy'
	node('master') {
     echo "deploying"
	}

