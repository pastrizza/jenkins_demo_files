node ('docker-slave-jnlp') {  
    stage('Clone') { 
        sh 'echo "Cloning............"'
        sh 'git clone git@github.com:pastrizza/jenkins_demo_scripts.git project'
        sh 'echo "Cloning complete"'
    }
    stage('Build') { 
        sh 'echo "Building......"'
                sh 'chmod -R +x project'
                sh 'project/build.sh > artifact.txt'
                sh 'echo "Build done"'
    }
    stage('Test') { 
         sh 'echo "Testing......"'
                sh 'project/test.sh > test_result.txt'
                sh 'echo "Testing done"'
    }
}