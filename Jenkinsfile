pipeline {
    agent {
        docker {
            image 'docker.io/krickwix/ybuild:v0.4'
            label 'great-bear-yocto-large'
        }
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split('/').size() > 1 ? GIT_BRANCH.split('/')[1..-1].join('/') : GIT_BRANCH}"
        GIT_HASH = GIT_COMMIT.take(7)
    }
    stages {
        stage("artefacts") {
            steps {
                withCredentials([[
                        $class: 'AmazonWebServicesCredentialsBinding',
                        credentialsId: "gbear-aws-eticloud-credentials",
                        accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                        secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh '''
                        set -x
                        cp dummyfile dummyfile.$GIT_HASH
                        aws s3 cp dummyfile.$GIT_HASH 's3://cisco-eti-gbear-scratch/test/'
                    '''
                }
            }
        }
    }
}