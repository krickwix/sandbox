@Library(['srePipeline', 'alcor-jenkins']) _

def params = [
  vault: [
    namespace: "eticloud/jenkins",
  ],
  region: [
    deploymentType: "dev"
  ],
]

pipeline {
    agent {
        docker { image 'docker.io/krickwix/ybuild:v0.3' }
		label 'great-bear-yocto-large' 
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split('/').size() > 1 ? GIT_BRANCH.split('/')[1..-1].join('/') : GIT_BRANCH}"
    }
    stages {
        stage("artefacts") {
            steps {
                awsLogin(params, roleName="jenkins-s3-full-access") {
                    aws s3 cp dummyfile s3://cisco-eti-gbear-scratch/test/dummyfile
                }
            }
        }
    }
}