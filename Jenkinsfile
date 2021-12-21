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
                        sh './gradlew sonarqube -dsonar.host.url="http://192.168.0.105:9000" -dsonar.login=fbe91d87bba09ddcce8c31acac0244054d625e26' 
                    }
                }
            }
           
        }
    }
}