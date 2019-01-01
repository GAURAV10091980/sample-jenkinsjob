@Library('pipeline-library-demo')_

def say(String name = 'human') {
  echo "Hello, ${name}."
  echo "Hello, ${name}."
}

node('maven-label') {
   def mvnHome
   
   stage('shard lib Demo') {

        echo 'Hello World'

        sayHello 'Dave'

}
   
   stage('reference lib Demo') {


        say 'Edureka'

}
   stage('Preparation') { // for display purposes
      
      git 'https://github.com/isandt/xcard.git'
             
      mvnHome = tool 'maven'
   }
   stage('Build') {
      
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}
