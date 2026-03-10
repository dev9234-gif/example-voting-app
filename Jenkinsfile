pipeline {
    agent { label 'worker' }

    stages {

        stage("Docker build and push") {
            steps {
                sh """
                docker login -u dev9234 -p Manjeet9234
                cd vote
                docker build -t dipesh017/vote:v${BUILD_NUMBER} .
                docker push dipesh017/vote:v${BUILD_NUMBER}
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
