pipeline {
    agent { label 'worker' }

    stages {

        stage("vote") {
            steps {
                sh """
                docker login -u dev9234 -p Manjeet9234
                cd vote
                docker build -t dev9234/vote:v${BUILD_NUMBER} .
                docker push dev9234/vote:v${BUILD_NUMBER}
                docker run -itd -p 81:80 dev9234/vote:v${BUILD_NUMBER}
                """
            }
        }
        stage("Result") {
            steps {
                sh """
                cd result
                docker build -t dev9234/result:v${BUILD_NUMBER} .
                docker push dev9234/result:v${BUILD_NUMBER}
                docker run -itd -p 82:80 dev9234/result:v${BUILD_NUMBER}
                """
            }
        }

        stage("Deploy") {
            steps {
                sh "echo docker deploy"
            }
        }
    }
}
