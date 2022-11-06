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
                    deploy adapters: [tomcat9(credentialsId: '9b11b714-2672-450b-82f7-3faf36d83932', path: '', url: 'http://localhost:8082/')], contextPath: null, war: '**/*.war'
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
    
        
               
            
                
                
        
