node {
 stage 'Build'
 env.PATH = "${tool 'Maven 3'}/bin:${env.PATH}"
 checkout scm
 sh 'mvn clean compile'
 stage 'Test'
 sh 'mvn test integration-test'
 stage 'Install'
 sh 'mvn install -DskipTests'

 step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar, **/target/*.hpi', fingerprint: true])
 step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
}
