pipeline{
    agent any
    tools {
        maven 'maven'
        jdk 'java'
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
        stage("Copy Docker file to Ansible serve"){
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//docker', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: 'webapp/target/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }            
        }
        stage("Copy Docker and Yaml file to Ansible server"){
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//docker', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '/var/lib/jenkins/workspace/project/files/*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }        
        }
        
    }
    
}