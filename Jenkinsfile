pipeline{
	agent any
	stages {
		stage('Checkout'){
			steps{
				git branch: 'main', url: 'https://github.com/LabWorksDai/model-train.git'
			}
		}
		stage('INstall Dependencies'){
			steps{
				sh'''	
    					python3 -m venv venv
					./venv/bin/activate
            				pip install -r requirements.txt
				'''
			}
		}
		stage('Train MOdel'){
			steps{
				sh '''
    				./venv/bin/activate
    				python3 train.py
				'''
			}
		}
		stage('Test MOdel'){
			steps{
				sh '''
    				./venv/bin/activate
    				python3 test.py
				'''
			}
		}
		stage('Archive MOdel'){
			steps{
				archiveArtifacts artifacts: 'model.pkl', fingerprint: true
			}
		}

	}
}
