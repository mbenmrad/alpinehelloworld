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
                        sh(script: sshCommand + " 'echo \"Contenu du fichier\" > /home/ubuntu/test.txt'", returnStatus: true)
                    } else {
                        error "Le credential SSH 'username' n'a pas été trouvé."
                    }
                }
            }
        }
    }
}
