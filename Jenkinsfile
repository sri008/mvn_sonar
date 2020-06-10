pipeline {
   agent any

   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/mvn_sonar.git'
         }
      }
      stage('Build Clean') {
         steps {
            sh label: '', script: '/opt/maven/bin/mvn clean deploy'
         }
      }
   }
}
