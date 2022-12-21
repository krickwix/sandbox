pipeline {
    agent {
        docker { 
		image 'docker.io/krickwix/ybuild:v0.5'
		label 'great-bear-yocto-large' 
    	}
    }
    stages {
        stage('cred') {
		steps {
	            withCredentials([file(credentialsId: 'mender-signing-key', variable: 'SIGNING_KEY')]) {
        	        sh '''
                	    echo "$SIGNING_KEY" > /tmp/test.key && cat /tmp/test.key
                	'''
		    }
            	}
        }
    }
}
