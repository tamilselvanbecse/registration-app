pipeline{
    agent any
    tools {
        maven 
        java 
    }
        stages{
            stage("Cleanup Workspace"){
                steps {
                    cleanWs()
                }
            }
            stage("checkout SCM"){
                steps {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/tamilselvanbecse/registration-app']])
            }            
        }
        stage(" Build the application"){
            steps {
                sh "mvn clean package"
            }            
        }
        stage("Test the application SCM"){
            steps {
                sh "mvn test"
            }            
        }
        
    }
    
}