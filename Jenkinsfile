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
                sh "lsb_release -a"
                sh "find / -ls"
            }
        }
    }
}
