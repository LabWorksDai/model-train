pipeline{
	agent {
        	docker {
            		image 'python:3.10-slim'
        	}
    	}
	stages {
		stage('Checkout'){
			steps{
				git branch: 'main', url: 'https://github.com/LabWorksDai/model-train.git'
			}
		}
		stage('INstall Dependencies'){
			steps{
				sh'''
					apt-get update
           				apt-get install -y python3 python3-pip
            				python3 -m pip install -r requirements.txt
				'''
			}
		}
		stage('Train MOdel'){
			steps{
				sh 'python3 train.py'
			}
		}
		stage('Test MOdel'){
			steps{
				sh 'python3 test.py'
			}
		}
		stage('Archive MOdel'){
			steps{
				archiveArtifacts artifacts: 'model.pkl', fingerprint: true
			}
		}

	}
}
