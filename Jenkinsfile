pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Gunakan URL HTTPS biasa tanpa credential
                git url: 'https://github.com/Ajaone/sast-demo-app.git', 
                     branch: 'master'
            }
        }
        
        stage('SAST Analysis') {
            steps {
                sh 'bandit -r . -f xml -o bandit-output.xml || true'
                recordIssues tools: [bandit(pattern: 'bandit-output.xml')]
            }
        }
    }
}
