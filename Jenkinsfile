pipeline{
  agent any
  stages{
  
    stage('Checkout'){
      steps{
      	git branch: 'main', url: 'https://github.com/LabWorksDai/model-train.git'
      }
    }
    
    stage('Install Dependencies'){
      steps{
        sh '''
            python3 -m venv venv
            . venv/bin/activate
            pip install -r requirements.txt
        '''
      }
    }
    
    stage('Train model'){
      steps{
        sh '''
            . venv/bin/activate
            python train.py
        '''
      }
    }
    
    stage('Test model'){
      steps{
        sh '''
            . venv/bin/activate
            python test.py
        '''
      }
    }
    
    stage('Archive model'){
      steps{
        archiveArtifacts artifacts: 'model.pkl',fingerprint:true
      }
    }
  }
}
