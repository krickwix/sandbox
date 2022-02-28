pipeline {
    agent {
          docker { image 'docker.io/krickwix/ybuild:v0.3' }
    }
    stages {
        stage("artefacts") {
            steps {
                minio bucket: 'sandbox',
                    credentialsId: 'minio_gbear-user',
                    targetFolder: 'jenkins-build/$BRANCH',
                    host: 'http://10.60.16.240:9199',
                    includes: 'dummyfile'
            }
    }
}