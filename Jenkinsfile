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
                       //sh 'curl -u admin:admin123 "http://192.168.1.107:9000"'
                       sh './gradlew sonarqube --stacktrace  -Dsonar.host.url="http://192.168.1.107:9000" --warning-mode all'
                                              
                    }
                }
            }
            
        }
    }
 
}