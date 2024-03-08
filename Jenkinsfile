pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the C++ file
                    sh 'g++ -o my_program pes2ug21cs419-1.cpp'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Print the output of the compiled program
                    sh './my_program'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Push the changes to the repository
                    gitPush()
                }
            }
        }
    }

    post {
        failure {
            echo 'pipeline failed'
        }
    }
}

def gitPush() {
    // Replace these values with your Git repository URL and credentials
    def gitUrl = 'https://github.com/your_username/your_repository.git'
    def gitCredentialsId = 'your_git_credentials_id'

    withCredentials([usernamePassword(credentialsId: gitCredentialsId, usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
        sh "git config --global user.email 'you@example.com'"
        sh "git config --global user.name 'Jenkins'"
        sh "git add ."
        sh "git commit -m 'Update C++ file'"
        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@${gitUrl}"
    }
}
