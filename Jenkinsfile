pipeline {
   agent any

   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/mvn_sonar.git'
         }
      }
      stage('Sonar') {
         steps {
            withSonarQubeEnv('sonar') {
                sh '/opt/maven/bin/mvn clean verify sonar:sonar -Dmaven.test.skip=true'
            }
         }
      }
      stage('Quality Gates') {
         steps {
            timeout(time: 1, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
            }
         }
      }
      stage('Build Clean') {
         steps {
            sh label: '', script: '/opt/maven/bin/mvn clean install'
         }
      }
   }
}
