pipeline {
    agent any
    stages {
        stage('Test'){
            steps{
                echo "Test skipped"
            }
        }

        stage('Deploy'){
            steps{
                echo "Test run"
                sh "chmod 755 deploy.sh"
                sh 'ssh root@localhost "bash -s" < deploy.sh'
            }
        }
    }
    
    post{
        success{
            echo 'Success'
            slackSend (color: '#00FF00', message: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        }
        failure {
            echo 'Failed'
            slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        }
        unstable {  
            echo 'Unstable'  
        }  
        changed {  
            echo 'State changed'  
        }
    }
}
