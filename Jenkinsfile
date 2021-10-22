pipeline{
    agent any
    stages{
        stage("sonar quality control"){
            agent{
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --stacktrace -Dsonar.host.url="http://192.168.1.107:9000" -Dsonar.login="admin" -Dsonar.password="admin123"'
                    }   
                }
            }
            
        }
    }
 
}