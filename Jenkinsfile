pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
            steps {
                sh 'git clone https://github.com/pastrizza/jenkins_demo_scripts.git'
                sh 'cd jenkins_demo_scripts'
                sh 'git branch'
                sh './build.sh > artifact.txt' 
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
