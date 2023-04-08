pipeline {
    agent any
    tools { nodejs "NodeJS (sern snippets)" }
    
    stages {
        stage('Build VSCode extension') {
            steps {
                // Clone the repository that contains the VSCode extension
                git branch: 'jenkins-testing', url: 'https://github.com/sern-handler/snippets.git'
                
                // Install dependencies
                sh 'npm install'

                sh 'npm i -g @vscode/vsce'
                
                // Build the extension
                sh 'vsce package'
                
                // Set the built file as an artifact
                archiveArtifacts artifacts: '*.vsix', onlyIfSuccessful: true
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
