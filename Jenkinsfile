pipeline {
    agent any
    
    tools {
        maven 'maven3'
    }
    
    
        
        stages {
            
            stage('Verify Maven installed') {
                steps {
                    sh 'mvn -v'
                }
            }
            
            stage ('Compile') {
                steps {
                    sh 'mvn clean compile'
                }
                
            }
            
            stage ('Test') {
                steps {
                    sh 'mvn test'
                }
                
            }
        }
        
        post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
                failure {
                    slackSend channel: 'jenkins-training', message: 'Sana -  marche pas stp!', teamDomain: 'devinstitut', tokenCredentialId: 'slack_token'
                }
                success {
                    slackSend channel: 'jenkins-training', color: '#439FE0', message: 'Sana -  marche stp!', teamDomain: 'devinstitut', tokenCredentialId: 'slack_token'
                }
        }
        
    
            
}
    
    


