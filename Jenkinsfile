pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: '13.38.120.217', keyFileVariable: 'UBUNTU')]) {
                        // Vous pouvez maintenant utiliser UBUNTU dans vos commandes SSH.
                        sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker run --name montest9 -d -p 8089:80 hello-world'"""
                         sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker ps'"""
                    }
                }
            }
        }
    }
}
