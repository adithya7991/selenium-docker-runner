/* 
Different approach followed below, bcz jenkins gets only 1 terminal
If v do just "docker-compose up", it will keep on running as grid is like a server,
Due to which jenkins cannot exec next commands
*/
pipeline{
    agent any
    stages{
        stage('Start Grid'){
            steps{
                bat "docker-compose up --no-color -d hub chrome firefox"

            }            
        }
        stage('Run Tests'){
            steps{
                bat "docker-compose up --no-color search-module book-flight-module"
            }   

        }
        /*
        Moving this stage under post, bcz if kill the job @ any stage, next stages will not b executed
        post with always acts like finally block, always executes
        stage('Stop Grid'){
            steps{
                bat "docker-compose down"
            }            
        }*/
    }
    post{
        always{
            archiveArtifacts artifacts: 'output[volume-mapped]/**'
            bat "docker-compose down"
        }
    }
}