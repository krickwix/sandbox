pipeline {
    agent {
        docker {
            image 'docker.io/krickwix/ybuild:v0.4'
            label 'great-bear-yocto-large'
        }
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split('/').size() > 1 ? GIT_BRANCH.split('/')[1..-1].join('/') : GIT_BRANCH}"
    }
    stages {
        stage("artefacts") {
            steps {
                sh '''
                    aws s3 cp dummyfile 's3://cisco-eti-gbear-scratch/test/dummyfile'
                '''
            }
        }
    }
}