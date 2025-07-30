pipeline {
    agent { label 'worker' }

    stages {
        stage('First Step') {
            steps {
                sh 'echo "First step"'
            }
        }

        stage('Second Step') {
            steps {
                sh 'echo "Second step"'
            }
        }
    }
}
