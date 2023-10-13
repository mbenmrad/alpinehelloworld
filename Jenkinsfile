pipeline {
    agent any

    stages {
        stage('SSH Command') {
            steps {
                script {
                    def sshCredential = credentials('ubuntu') // Remplacez 'username' par le nom de votre credential

                    if (sshCredential != null) {
                        def sshCommand = "ssh -i ${sshCredential} ubuntu@ec2-35-180-174-196.eu-west-3.compute.amazonaws.com"

                        // Exécutez la commande SSH
                         def sshOutput = sh(script: "${sshCommand}", returnStdout: true)

                        echo "Liste des fichiers sur l'instance distante :"
                        echo sshOutput
                    } else {
                        error "Le credential SSH 'username' n'a pas été trouvé."
                    }
                }
            }
        }
    }
}
