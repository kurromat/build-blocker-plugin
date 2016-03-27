node {
 stage 'Build'
 env.PATH = "${tool 'Maven 3'}/bin:${env.PATH}"
 checkout scm
 mvn 'clean compile'
 
 stage 'Test'
 mvn 'test'
 
 stage 'IntegrationTest'
 mvn 'verify'
 
 stage 'Install'
 mvn 'install -DskipTests'

 step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar, **/target/*.hpi', fingerprint: true])
 step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
}

def mvn (args){
 sh "${tool 'Maven 3'}/bin/mvn ${args}"
}
