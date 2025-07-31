pipeline {
    agent { label 'worker' }
    options { buildDiscarder(logRotator(numToKeepStr: '15'))
              disableConcurrentBuilds() 
              retry(2)
              timeout(time: 10, unit: 'MINUTES') 
            }
     parameters { booleanParam(name: 'BRANCH', defaultValue: true, description: '') }
     triggers { pollSCM('* * * * *') }
    stages {
        stage('First Step') {
            steps {
                sh 'docker login -u dev9234 -p Manjeet9234'
                sh '''
                cd vote 
                docker build -t dev9234/pipeline:v$BUILD_NUMBER .
                   '''
                sh 'docker push dev9234/pipeline:v$BUILD_NUMBER'
            }
        }

        stage('Second Step') {
            steps {
                sh 'echo "Second step"'
            }
        }
    }
}
