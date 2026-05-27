pipeline {
    agent any

    options {
        ansiColor('xterm')
    }

    environment {
        DEPLOY_NAME = 'DECISION'
        DEPLOY_OPTS = ['dev', 'staging', 'prod']
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    def respuesta = input(
                        message: "¿Desplegar en producción?",
                        parameters: [
                            choice(name: $env.DEPLOY_NAME, choices: $env.DEPLOY_OPTS, description: "Selecciona opción")
                        ]
                    )

                    if (respuesta.$env.DEPLOY_NAME == env.DEPLOY_OPTS[0]) {
                        echo "\033[1;31mDesplegando en desarrollo...\033[0m"
                    } else if (respuesta.$env.DEPLOY_NAME == env.DEPLOY_OPTS[1]) {
                        echo "\033[1;31mDesplegando en preproducción...\033[0m"
                    } else if (respuesta.$env.DEPLOY_NAME == env.DEPLOY_OPTS[2]) {
                        echo "\033[1;31mDesplegando en producción...\033[0m"
                    } else {
                        //echo "\033[1;32mDesplegando en ${respuesta.$env.DEPLOY_NAME}...\033[0m"
                        echo "\033[1;32mSelecciona una opción válida\033[0m"
                    }
                    //echo "\033[1;34mEste es un mensaje desde el Jenkinsfile\033[0m"
                    //sh 'echo -e "\\033[1;34mEjecutando comando dentro del pipeline\\033[0m"'
                }
            }
        }
    }
}
