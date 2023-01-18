pipeline{
    agent any
    tools {
  maven 'maven3'
}

    stages{
        stage("git-checkout"){
            steps{
                git branch: 'main', credentialsId: 'git-id', url: 'https://github.com/kirantamatam/git-app.git'
            }
        }
        stage("maven-build"){
            steps{
                sh 'mvn package'
            }
        }
         
        stage("nexus-upload"){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'restapi', classifier: '',
                file: 'target/restapi-0.0.3-SNAPSHOT.jar', type: 'jar']], credentialsId: 'Nexusid',
                groupId: 'com.example', 
                nexusUrl: '172.31.85.190:8081', nexusVersion: 'nexus3', 
                protocol: 'http', repository: 'app-snapshot', version: '0.0.3-SNAPSHOT'
            }
        }
        
            
    }
            
 }
