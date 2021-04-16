pipeline {
    agent any
    stages {
        stage("SCM"){
            steps {
                git credentialsId: 'GITHUB_ID', url: 'https://github.com/cisco00/kubernetes-files.git'
            }
        }
        stage("initial setup"){
            steps{
                ansiblePlaybook credentialsId: 'devnode', disableHostKeyChecking: true, installation: 'ansible', inventory: 'k8s.inv', playbook: 'initial-setup.yml'
            }
            
        }
        stage("Docker Push"){
            steps{
                ansiblePlaybook credentialsId: 'devnode', disableHostKeyChecking: true, installation: 'ansible', inventory: 'k8s.inv', playbook: 'dependency.yml'
            }
        }
    }
}
         
