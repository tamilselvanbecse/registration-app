pipeline{
    agent any
    tools {
        maven 'Maven 3.9.4' 
        jdk 'Java 17.0.8' 
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