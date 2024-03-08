pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                // It seems like you want to build a project called 'PES2UG21CS006-1'. 
                // If it's a Jenkins job, use 'build' step to trigger it.
                build 'PES2UG21CS419-1'
                
                // Assuming 'main.cpp' is part of the project being built, 
                // ensure that the build job generates the 'main.cpp' file or it's available in the workspace.
                
                // If 'main.cpp' is a part of the current workspace, you can directly compile it.
                sh 'g++ main.cpp -o output'
            }
        }

        stage('Test') {
            steps { 
                // Assuming 'output' is the compiled executable.
                // You should navigate to the directory where the executable is located before executing it.
                dir ('.') {
                    sh './output'
                }
            }
        }

        stage('Deploy') { 
            steps { 
                echo 'Deployed' 
            } 
        } 

    } 

    post { 
        failure { 
            error 'Pipeline failed' 
        }  
    }  
}
