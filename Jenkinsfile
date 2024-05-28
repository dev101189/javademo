pipeline{
    agent any
    stages{
        stage("Getting Project URL"){
           steps {
               sh 'echo ${projectUrl}'
           }
        }
        stage("Checkout the code"){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: '${projectUrl}']])
            }
        }
        stage("Package the Project"){
            steps{
                sh 'mvn package'
                sh 'cat Jenkinsfile'
            }
        }
    }
    post { 
        always { 
           cleanWs()
        }
    }
}
