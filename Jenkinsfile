pipeline {
steps {
 script {
  withCredentials([sshUserPrivateKey(credentialsId: '13.38.120.217', keyFileVariable: 'UBUNTU')]) {
  // Vous pouvez maintenant utiliser PRIVATE_KEY dans vos commandes SSH.
   sh "ssh -i $UBUNTU ubuntu@ec2-13-38-120-217.eu-west-3.compute.amazonaws.com 'docker ps -a'"
            }
        }
}
}
