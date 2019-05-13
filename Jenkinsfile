node {
    stage('scm checkout for api test'){
    git credentialsId: '2bf8a43e-4698-4cd4-a5b5-4109e16794b9', url: 'https://github.com/rkidambi11/maven.git'
}
    stage ('maven package'){
    echo " API package will going to start"
    def mvnHome=tool name: 'M3', type: 'maven'
    sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
    }
    stage('Test')   {
   //Perform test
   echo 'Execute the script'
    def mvnHome=tool name: 'M3', type: 'maven'
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore test"
  }
  stage('Results') {
  junit '**/target/surefire-reports/TEST-*.xml'
  archive 'target/*.jar'
}
}
