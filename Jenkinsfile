pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                git branch: 'main', url: 'https://github.com/kanaka2024/postmantrialversion.git'
            }
        }

        stage('Install Newman') {
            steps {
                // Install Newman globally
                sh 'npm install -g newman'
            }
        }

        stage('Run Postman Tests') {
            steps {
                // Run the Postman collection using Newman
                sh 'newman run ProgramBatch.postman_collection.json -e Team10_PostmanPatrollers.postman_environment.json'
            }
        }
    }

    post {
        always {
            // Archive test results (optional)
            archiveArtifacts artifacts: 'newman/*.json', allowEmptyArchive: true
        }
    }
}