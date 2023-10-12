pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ec2-arm64'
    }
    stages {
        stage('test') {
            when {
                not { branch 'master' }
            }

            steps {
                sh "uname -a"
                sh "docker build -t docker/getting-started ."
                sh "docker image ls"
            }
        }
        stage('build and push') {
            when {
                branch 'master'
            }

            steps {
                sh "docker build -t docker/getting-started ."
                withDockerRegistry([url: "", credentialsId: "dockerbuildbot-index.docker.io"]) {
                    sh("docker push docker/getting-started")
                }
            }
        }
    }
}
