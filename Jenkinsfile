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
                        sh 'echo "hello"'
                        sh 'curl http://192.168.1.107:9000'
                        sh './gradlew sonarqube  -Dsonar.host.url="http://192.168.1.107:9000" -Dsonar.login=e2a7a0713476a174e7c2ca56f6129491a8527d39'
                    }   
                }
            }
            
        }
    }
 
}