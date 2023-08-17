pipeline{
    agent any
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
        
        }
    
}