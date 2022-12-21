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
	            withCredentials([file(credentialsId: 'mender-signing-key', variable: 'signing-key')]) {
        	        sh '''
                	    echo "$signing-key" > /tmp/test.key && cat /tmp/test.key
                	'''
		    }
            	}
        }
    }
}
