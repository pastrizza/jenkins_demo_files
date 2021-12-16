pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
            steps {
                sh 'git clone https://github.com/pastrizza/jenkins_demo_scripts.git project'
                sh 'chmod -R +x project/'
                sh 'ls -la project'
                sh 'project/build.sh' 
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
