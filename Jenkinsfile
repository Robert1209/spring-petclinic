pipeline {
   agent any

   stages {
      stage('Build') {
         steps {
            sh 'mvn package'
            script {
               withSonarQubeEnv() {
                  sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
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
