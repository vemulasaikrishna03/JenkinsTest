pipeline {
    agent any

    stages {
        stage('Set Branch Name') {
            steps {
                script {
                    def branchFile = readFile('./file')
                    def branchName = branchFile.trim()
                    env.BRANCH_NAME = branchName
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
                // steps
            }
        }
    }
}
