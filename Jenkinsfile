pipeline {
    agent any

    options {
        ansiColor('xterm')
    }

    environment {
        DEPLOY_NAME = 'DECISION'
        DEPLOY_OPTS = "dev,staging,prod"
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    def opciones = env.DEPLOY_OPTS.split(',')

                    def respuesta = input(
                        message: "¿Desplegar en producción?",
                        parameters: [
                            choice(
                                name: $env.DEPLOY_NAME,
                                choices: opciones.join('\n'),
                                description: "Selecciona opción"
                            )
                        ]
                    )

                    if (respuesta == opciones[0]) {
                        echo "\033[1;31mDesplegando en desarrollo...\033[0m"
                    } else if (respuesta == opciones[1]) {
                        echo "\033[1;31mDesplegando en preproducción...\033[0m"
                    } else if (respuesta == opciones[2]) {
                        echo "\033[1;31mDesplegando en producción...\033[0m"
                    } else {
                        echo "\033[1;32mSelecciona una opción válida\033[0m"
                    }
                    //echo "\033[1;34mEste es un mensaje desde el Jenkinsfile\033[0m"
                    //sh 'echo -e "\\033[1;34mEjecutando comando dentro del pipeline\\033[0m"'
                }
            }
        }
    }
}
