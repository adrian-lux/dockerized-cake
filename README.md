# CakePHP Docker Container

CakePHP living inside a docker container.

Todo:
Set up Jenkins so that it runs the following commands when the repository is updated assuming the desired port is 80 and the desired project name is "carrot-cake." Realistically the project name should be something to help us identify its connection with the repo branch, and the port should be something unique from the other branches.

    echo "port=80" > .env
    docker-compose -p carrot-cake build
    docker-compose -p carrot-cake uo -d
