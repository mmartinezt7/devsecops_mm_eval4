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
                      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=tarea4-devsecops -Dsonar.sources=target/ -Dsonar.host.url=http://192.168.8.112:9000 -Dsonar.login=220d8b11c0d69a6137dae715e362b72d711a2a9e"
                    }
                }
           }
        }
    }
}
