pipeline{
    agent any
    parameters {string defaultValue: 'https://github.com/cloud-dev-user/javademo.git', name: 'projectUrl' }
    stages{
        stage("Getting Project URL"){
           steps {
               sh 'echo $projectUrl'
           }
        }
        stage("Checkout the code"){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: '$projectUrl']])
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
