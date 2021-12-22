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
                        sh './gradlew sonarqube -Dsonar.login=admin -Dsonar.password=admin1' 
                    //}
                    timeout(time: 1, unit: 'HOURS') {
                        def qg = waitForQualityGate()
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due quality gate failure: ${qg.status}"
                        }
                    }
                }
            }
           
        }
    }
}