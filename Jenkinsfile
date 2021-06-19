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
                    mvn sonar:sonar \
					  -Dsonar.projectKey=tarea4-devsecops \
					  -Dsonar.host.url=http://localhost:9000 \
					  -Dsonar.login=a6fcda4a095545489be1a8833ab1ad21452b3ed0
					
                }
           }
        }
    }
}
