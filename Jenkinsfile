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
                    //withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --info -Dsonar.login="admin" -Dsonar.password="admin1"     ' 
                    //}
                }
            }
           
        }
    }
}