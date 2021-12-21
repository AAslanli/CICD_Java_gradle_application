pipeline{
    agent any 
    stages{
        stage("Sonar Quality Check"){
            agent {
                docker {
                    image 'openjdk:11'
                    args '-u root:root'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube -Dsonar.login=5ef15ea7d699edb30c4b94912bbebdde98e7ffec' 
                    }
                }
            }
           
        }
    }
}