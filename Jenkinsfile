pipeline {
    agent { label 'docker-slave-ssh' }
    stages {
        stage('Clone') {
            steps {
                sshagent(credentials: ['github-ssh']) {
                    sh 'git clone git@github.com:pastrizza/jenkins_demo_scripts.git project'
                    sh 'git checkout -t -b $GITHUB_PR_SOURCE_BRANCH origin/$GITHUB_PR_SOURCE_BRANCH'
                    sh 'git merge $GITHUB_BRANCH'
                    sh 'cat project/README'
                }
            }

        }
        stage('Build') {
            steps {
                sh 'echo "Building......"'
                sh 'project/build.sh > artifact.txt'
                sh 'echo "Build done"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing......"'
                sh 'project/test.sh'
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
