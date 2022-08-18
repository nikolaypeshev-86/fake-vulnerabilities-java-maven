node {
  stage('source') {
    git 'https://github.com/nikolaypeshev-86/fake-vulnerabilities-java-maven.git'
  }
  stage('SonarQube Analysis') {
  withSonarQubeEnv('sq19') {
	addALMOctaneSonarQubeListener pushCoverage: true, pushVulnerabilities:true, sonarToken:'squ_1718dd56ef3addd539609b7b09674e9a706b9a5f' , sonarServerUrl:'http://bgsovm00017.corp.polygran.de:9000'
	sh(returnStatus: true, script: "mvn clean install sonar:sonar -Dsonar.projectKey=Vulnerabilities -Dsonar.host.url=http://bgsovm00017.corp.polygran.de:9000 -Dsonar.login=sqp_6a4d29cc0fefa465dbe459ea8f9792e922a23ed7 -Dsonar.analysis.buildNumber=${BUILD_NUMBER} -Dsonar.analysis.jobName=${JOB_NAME}")
}
  }
}
