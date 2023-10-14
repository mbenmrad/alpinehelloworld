pipeline {
agent any
stages {
stage('Deploy') {
steps {
 script {
  withCredentials([sshUserPrivateKey(credentialsId: 'monid', keyFileVariable: 'idssh')]) {
  // Vous pouvez maintenant utiliser PRIVATE_KEY dans vos commandes SSH.
   sh "ssh -i \$idssh ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker ps -a'"
            }
        }
}
}
}
}
