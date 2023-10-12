pipeline {
    agent any
    stages {
        stage('Exécution SSH') {
            steps {
                script {
                    sshUserPwdCredentials = credentials('idSSH') // Utilisez le nom du credential créé
                    echo "Nom d'utilisateur du credential : ${sshUserPwdCredentials.username}"
                    sh """
                        echo "Nom d'utilisateur du credential : ${sshUserPwdCredentials.username}"
                    """
                }
            }
        }
    }
}

