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
                sh """mvn package -e"""
            }
        }
        
        stage("MVN Clean"){
            steps {
                sh """mvn clean -e """
                
            }
        }

         stage("MVN Compile"){
            steps {
                sh """mvn compile -e """
                
            }
        }

           stage("MVN install"){
            steps {
                sh """mvn install  """
                
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

        stage("DEPLOY with Nexus") {
            steps { 
                sh'mvn clean deploy -Dmaven.test.skip=true -Dresume=false'
            }
        }

    
        
        
        
        
        
    }

}