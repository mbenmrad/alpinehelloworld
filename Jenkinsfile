pipeline {
    agent any
    stages {
        stage('Exécution SSH') {
            steps {
                script {
                    sshUserPwdCredentials = credentials('idSSH') // Utilisez le nom du credential créé
                    sh """
                     echo "Nom d'utilisateur du credential : ${sshUserPwdCredentials.username}"
                     ssh -i ${sshUserPwdCredentials.idSSH} ubuntu@ec2-35-180-138-82.eu-west-3.compute.amazonaws.com
                     mkdir test
                    """
                }
            }
        }
    }
}

