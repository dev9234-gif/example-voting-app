pipeline {
    agent { label 'worker' }

    stages {

        stage("Docker build and push") {
            steps {
                sh """
                docker login -u dipesh017 -p Arvi
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
