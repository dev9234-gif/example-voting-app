pipeline {
    agent { label 'worker' }
    options { buildDiscarder(logRotator(numToKeepStr: '15'))
              disableConcurrentBuilds() 
              retry(2)
              timeout(time: 10, unit: 'MINUTES') 
            }
     parameters { booleanParam(name: 'BRANCH', defaultValue: true, description: '')
                choice(name: 'ENV', choices: ['dev', 'qa', 'uat'], description: '')
                }
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
                sh 'docker run -itd -p 81:80 dev9234/pipeline:v$BUILD_NUMBER '
            }
        }        
        stage('run testing') {
        when {
            expression { params.ENV == 'qa' }
        }
        
             parallel {
        stage('Second Step') {
            steps {
                sh 'echo "Second step"'
            }
        }
                stage('third Step') {
            steps {
                sh 'echo "Second step"'
            }
        }
            }
        }
        
    }
}
