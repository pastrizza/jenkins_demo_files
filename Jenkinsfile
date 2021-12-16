pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
<<<<<<< HEAD
            steps {
                sh 'git clone https://github.com/pastrizza/jenkins_demo_scripts.git'
                sh 'git branch'
                sh './build.sh > artifact.txt' 
            }
=======
          steps {
              script {  
                withCredentials([sshUserPrivateKey(credentialsId: 'git-hub-key', keyFileVariable: '')]) {
                    sh 'git clone git@github.com:pastrizza/jenkins_demo_files.git'
                    sh 'git branch'
                    sh './build.sh > artifact.txt' 
                } 
              }
           }
>>>>>>> 09d554c87615ac141c88078966bfca52c3e17794
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
