node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/abarazarte/jenkins-test.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven-3.5.3'
   }
   stage('Build') {
      sh "'${mvnHome}/bin/mvn' -B -DskipTests clean package"
   }
   stage('Tests') {
        sh "'${mvnHome}/bin/mvn' test"
        junit '**/target/surefire-reports/TEST-*.xml'
   }
   stage('Deliver'){
        archive 'target/*.jar'
        sh "'${mvnHome}/bin/mvn' jar:jar install:install help:evaluate -Dexpression=project.name"
   }
}
