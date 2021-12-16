pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
          steps {
              script {  
                withCredentials([sshUserPrivateKey(credentialsId: 'git-hub-key', keyFileVariable: '')]) {
                    sh 'git clone git@github.com:pastrizza/jenkins_demo_files.git'
                    sh 'git branch'
                    sh './build.sh > artifact.txt' 
                } 
              }
           }
        }
        stage('Build') {
            steps {
                sh 'echo "Build..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing"'
            }
        }
    }
    post {
        always {
            archiveArtifacts 'artifact.txt'
        }
    }
}
