pipeline {
    agent any

    options {
        ansiColor('xterm')
    }

    stages {
        stage('Imprimir comando') {
            steps {
                echo "\033[1;34mEste es un mensaje desde el Jenkinsfile\033[0m"
                sh 'echo -e "\\033[1;34mEjecutando comando dentro del pipeline\\033[0m"'
            }
        }
    }
}
