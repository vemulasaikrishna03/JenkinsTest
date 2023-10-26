pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your Git repository, replacing the URL with your own value
                script {
                    def branchFile = readFile('./file')
                    def branchName = branchFile.trim()
                    env.BRANCH_NAME = branchName
                    sh "git clone -b ${branchName} https://github.com/your/repo.git"
                }
            }
        }

        stage('Print Branch') {
            steps {
                script {
                    // Change to the Git repository directory
                    dir('repo') {
                        // Get the name of the current branch
                        sh 'git rev-parse --abbrev-ref HEAD'
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up, remove the cloned repository
            deleteDir()
        }
    }
}
