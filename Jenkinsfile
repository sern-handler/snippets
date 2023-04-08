pipeline {
    agent any
    
    stages {
        stage('Build VSCode extension') {
            steps {
                // Clone the repository that contains the VSCode extension
                git 'https://github.com/username/repo.git'
                
                // Install dependencies
                sh 'npm install'
                
                // Build the extension
                sh 'vsce package'
                
                // Set the built file as an artifact
                archiveArtifacts artifacts: 'my-extension.vsix', onlyIfSuccessful: true
            }
        }
        
        /* stage('Send webhook request') {
            steps {
                // Use curl to send a POST request to https://api.example.com
                sh 'curl -X POST https://api.example.com --data-urlencode "payload={\\"text\\":\\"New VSCode extension build available!\\"}"'
            }
        } */
    }
}
