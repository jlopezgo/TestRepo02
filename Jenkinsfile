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
                        message: "¿Deseas continuar con el despliegue?",
                        parameters: [
                            choice(
                                name: env.DEPLOY_NAME,
                                choices: opciones.join('\n'),
                                description: "Selecciona opción"
                            )
                        ]
                    )

                    switch (respuesta) {
                        case opciones[0]:
                            echo "\033[1;31mDesplegando en desarrollo...\033[0m"
                            break

                        case opciones[1]:
                            echo "\033[1;31mDesplegando en preproducción...\033[0m"
                            break

                        case opciones[2]:
                            echo "\033[1;31mDesplegando en producción...\033[0m"
                            break

                        default:
                            echo "\033[1;32mSelecciona una opción válida\033[0m"
                    }
                    //echo "\033[1;34mEste es un mensaje desde el Jenkinsfile\033[0m"
                    //sh 'echo -e "\\033[1;34mEjecutando comando dentro del pipeline\\033[0m"'
                }
            }
        }
    }
}
