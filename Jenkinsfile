node {
 stage 'Build'
 env.PATH = "${tool 'Maven 3'}/bin:${env.PATH}"
 checkout scm
 sh 'mvn clean compile'
 sh 'ls target'
 stage 'Test'
 sh 'mvn clean package'
 sh 'ls target'
 step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar', fingerprint: true])
 step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
}
