pipeline {
    agent {
          docker { image 'docker.io/krickwix/ybuild:v0.3' }
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split('/').size() > 1 ? GIT_BRANCH.split('/')[1..-1].join('/') : GIT_BRANCH}"
    }
    stages {
        stage("artefacts") {
            steps {
                minio bucket: 'sandbox',
                    credentialsId: 'minio_gbear-user',
                    targetFolder: 'jenkins-build/'+BRANCH_NAME,
                    host: 'http://10.60.16.240:9199',
                    includes: 'dummyfile'
            }
        }
    }
}