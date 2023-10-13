pipeline {
    agent any

    stages {
        stage('SSH Command') {
            steps {
                script {
                    def sshCredential = credentials('ubuntu')

                    if (sshCredential != null) {
                        echo "Nom d'utilisateur : ${sshCredential}"
                        def sshCommand = "ssh -i ${sshCredential} ubuntu@ec2-35-180-174-196.eu-west-3.compute.amazonaws.com"

                        // Exécutez la commande SSH pour lister les fichiers et stockez la sortie dans la variable stdout
                        def stdout = sh(script: sshCommand + " 'ls'", returnStdout: true).trim()

                        echo "Liste des fichiers sur l'instance distante :"
                        echo stdout
                    } else {
                        error "Le credential SSH 'ubuntu' n'a pas été trouvé."
                    }
                }
            }
        }
    }
}
