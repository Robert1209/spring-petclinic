pipeline {
   agent any

   stages {
      stage('Build') {
         steps {
            sh 'mvn package'
            script {
               withSonarQubeEnv() {
                  sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
               }

               docker.build("spring-petclinic:${env.BUILD_ID}")
            }
         }
      }
      stage('Run container') {
         steps {
            sh "docker run -d -p 8081:8080 spring-petclinic:${env.BUILD_ID}"
         }
      }
   }
}
