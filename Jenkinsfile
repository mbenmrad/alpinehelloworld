pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: '13.38.120.217', keyFileVariable: 'UBUNTU')]) {
                        // Vous pouvez maintenant utiliser UBUNTU dans vos commandes SSH.
                        sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker run -d -p 8083:80 mrad90/alpinehelloworld'"""
                         sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker ps'"""
                    }
                }
            }
        }
    }
}
