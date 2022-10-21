pipeline {
    agent any

   

    stages {
        stage('Git') {
            steps {
            
                git branch: 'main', url: 'https://github.com/Fatmanagati/testTpAchatFull.git',
                credentialsId : 'a67e0bc0-1dd1-4b3f-bdfb-85be76c0bd15'
                
            }

           
        }
        stage('MVN Package'){
            steps {
                sh """mvn -version  """
                sh """java -version """
            }
        }
        
        stage("MVN Clean"){
            steps {
                sh """mvn clean """
                
            }
        }

       stage('sonar'){
            steps {
                script{ withSonarQubeEnv('sonarQube') {
                     sh """mvn sonar:sonar -DskipTests""" 
                 }
               
                }
            }
        }

    
        
        
        
        
        
    }

}