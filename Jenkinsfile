pipeline {
    agent any

    tools {
        maven 'Maven'
        nodejs "NodeJs"
    }

    stages {
      stage ('Initial') {
            steps {
              echo '========================================='
              echo '                INITIAL '
              echo '========================================='
              sh '''
                   echo "PATH = ${PATH}"
                   echo "M2_HOME = ${M2_HOME}"
               '''
            }
        }
        stage ('Compile') {
            steps {
                echo '========================================='
                echo '                COMPILE '
                echo '========================================='
                 sh 'mvn clean compile -e'
            }
        }
        stage ('Test') {
            steps {
                echo '========================================='
                echo '                TEST '
                echo '========================================='
                 sh 'mvn clean test -e'
            }
        }
        
        stage('SonarQube analysis') {
           steps{
               echo '========================================='
              echo '                SONARQUBE '
              echo '========================================='
                script {
                    def scannerHome = tool 'sonar-scanner';
                    withSonarQubeEnv('Sonar Server') {
                      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Ms-Maven -Dsonar.sources=target/ -Dsonar.host.url=http://localhost:9000 -Dsonar.login=14c09fa032024d6f0e5923c7cead79f0bcaa23f3"
                    }
                }
           }
        }

 
    }
}
