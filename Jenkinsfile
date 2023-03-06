pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'raji_git', url: 'https://github.com/rajeeb007/lastautomation.git'
            }
        }
        stage('UNIT test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('maven build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Sonarqube') {

            environment {
            scannerHome = tool 'sonarqube'
         }
          steps {

            withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
             }
          timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
           }
         }
        }
        
    }
}