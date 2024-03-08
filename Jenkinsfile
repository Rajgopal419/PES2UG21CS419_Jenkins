pipeline {
    agent any 
    stages {
        
        stage('Build') {
            steps {
                build 'pes2ug21cs419-1'
                sh 'g++ main/hello.cpp -o output'
            }
        }

        stage('Test') {
            steps { 
                sh './output'
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
