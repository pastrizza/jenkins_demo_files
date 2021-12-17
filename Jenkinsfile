pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
            steps {
                sshagent(credentials: ['github-ssh']) {
                    sh 'echo "Cloning............"'
                    sh 'git clone -b $ghprbSourceBranch git@github.com:pastrizza/jenkins_demo_scripts.git project'
                    sh 'echo "Cloning complete"'
                }
            }

        }
        stage('Build') {
            steps {
                sh 'echo "Building......"'
                sh 'chmod -R +x project'
                sh 'project/build.sh > artifact.txt'
                sh 'echo "Build done"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing......"'
                sh 'project/test.sh > test_result.txt'
                sh 'echo "Testing done"'
            }
        }
    }
    post {
        always {
            archiveArtifacts 'artifact.txt'
        }
        failure {
            archiveArtifacts 'test_result.txt'
        }
    }
}
