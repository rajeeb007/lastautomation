pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'raji_git', url: 'https://github.com/rajeeb007/lastautomation.git'
            }
        }
    }
}