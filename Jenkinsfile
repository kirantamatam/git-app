pipeline{
    agent any
    tools {
  maven 'maven3'
          }

    stages{
        stage("git-checkout"){
            steps{
                git branch: 'main', credentialsId: 'kiran', url: 'https://github.com/kirantamatam/git-app.git'
            }
        }
        stage("maven-build"){
            steps{
                sh 'mvn package'
            }
        }
    }
}
