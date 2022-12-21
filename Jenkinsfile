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
	            withCredentials([string(credentialsId: 'hosted-mender-token', variable: 'TOKEN')]) {
        	        sh '''
                	    echo $TOKEN
                	'''
		    }
            	}
        }
    }
}
