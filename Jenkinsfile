pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages{
        stage ('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }   
        stage ('Deploy') {
            parallel {
                stage ('Deploy the staging') {
                  steps {
                    bat 'the is deploy stage'
                  }
                }
                stage ('Deploy to production') {
                    steps {
                        bat 'the is deploy to prod'
                    }
                }
            }
        }
    }
}  
    
        
               
            
                
                
        
