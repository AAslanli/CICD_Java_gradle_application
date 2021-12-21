pipeline{
    agent any 
    stages{
        stage("Sonar Quality Check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod +x gradlew'
                        sh 'curl http://192.168.0.105:9000/api/system/health'
                        sh './gradlew sonarqube --debug  ' 
                    }
                }
            }
           
        }
    }
}