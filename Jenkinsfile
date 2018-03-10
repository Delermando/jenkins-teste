stage 'Checkout'
 node('slave') {
  deleteDir()
  checkout scm
}

stage 'Build & Archive Apk'
 node('slave') {
  sh 'export ANDROID_SERIAL=192.168.56.101:5555 ; echo $ANDROID_SERIAL > build.txt'
  step([$class: 'ArtifactArchiver', artifacts: 'build.txt'])
 }

#stage 'Run Tests'
# node('slave') {
#  #sh 'export ANDROID_SERIAL=192.168.56.101:5555 ; ./runtests.sh'
#  publishHTML(target: [reportDir: 'meu_aplicativo_testes/build/reports/androidTests/connected/', reportFiles: 'index.html', reportName: 'Testes Instrumentados'])
#  #step([$class: 'JUnitResultArchiver', testResults: 'meu_aplicativo_testes/build/outputs/androidTest-results/connected/*.xml'])
#}	