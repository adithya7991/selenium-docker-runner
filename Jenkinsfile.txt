/* 
Different approach followed below, bcz jenkins gets only 1 terminal
If v do just "docker-compose up", it will keep on running as grid is like a server,
Due to which jenkins cannot exec next commands
*/
pipeline{
    stages{
        stage("Start Grid"){
            bat "docker-compose up --no-color -d hub chrome firefox"
        }
        stage("Run Tests"){
            bat "docker-compose up --no-color search-module book-flight-module"

        }
        stage("Stop Grid"){
            bat "docker-compose down"
        }
    }
}