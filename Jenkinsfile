
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your Git repository, replacing the URL and branch with your own values
                script {
                    def branchFile = readFile('./file')
                    def branchName = branchFile.trim()
                    sh "git clone -b ${branchName} https://github.com/vemulasaikrishna03/JenkinsTest.git"
                }
            }
        }

        stage('List Files') {
            steps {
                script {
                    // Change to the Git repository directory
                    dir('repo') {
                        // List all files in the branch
                        sh "git ls-tree --name-only HEAD"
                    }
                }
            }
        }
    }
    stage('Retrieve Changes') {
            steps {
                script {
                    // Change to the Git repository directory
                    dir('repo') {
                        // Fetch the latest changes from the remote repository
                        sh 'git fetch'
                        
                        // Get the list of changed files between the current branch and its remote counterpart
                        sh 'git diff --name-only @{u} HEAD'
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
