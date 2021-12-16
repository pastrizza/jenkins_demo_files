pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
            steps {
                sh 'git clone https://github.com/pastrizza/jenkins_demo_scripts.git project'
                sh 'chmod -R +x project/'
                sh 'git branch'
                sh 'git merge origin/main'
            }

        }
        stage('Build') {
            steps {
                sh 'echo "Building......"'
                sh 'git project/build.sh > artifact.txt'
                sh 'echo "Build done"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing......"'
                sh 'git project/test.sh'
                sh 'echo "Testing done"'
            }
        }
    }
    post {
        always {
            archiveArtifacts 'artifact.txt'
        }
    }
}
