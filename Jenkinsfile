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
                    withSonarQubeEnv(credentialsId: 'sonar-jenkins') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube ' 
                    }
                    timeout(time: 1, unit: 'HOURS') {
                        def qg = waitForQualityGate()
                         if (qg.status != 'OK') {
                           error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        }
                    }
                }
            }
           
        }
    }
}