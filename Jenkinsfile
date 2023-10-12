pipeline {
    agent any
    stages {
        stage('Exécution SSH') {
            steps {
                script {
                    sshUserPwdCredentials = credentials('idSSH') // Utilisez le nom du credential créé
                    sh """
                        echo "Hello"
                    """
                }
            }
        }
    }
}

