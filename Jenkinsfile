pipeline {
    agent any

   
    stages {
     
       


        stage('SonarQube analysis - SAST') {
           steps{
               echo '========================================='
              echo '                SONARQUBE '
              echo '========================================='
                script {
                    def scannerHome = tool 'sonar-scanner';
                    withSonarQubeEnv('SonarQube') {
                      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=tarea4-devsecops -Dsonar.sources=target/ -Dsonar.host.url=http://192.168.8.112:9000 -Dsonar.login=14c09fa032024d6f0e5923c7cead79f0bcaa23f3"
                    }
                }
           }
        }
    }
}
