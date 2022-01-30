/* 
Different approach followed below, bcz jenkins gets only 1 terminal
If v do just "docker-compose up", it will keep on running as grid is like a server,
Due to which jenkins cannot exec next commands
*/
Pipeline{
    Stages{
        Stage("Start Grid"){
            bat "docker-compose up --no-color -d hub chrome firefox"
        }
        Stage("Run Tests"){
            bat "docker-compose up --no-color search-module book-flight-module"

        }
        Stage("Stop Grid"){
            bat "docker-compose down"
        }
    }
}