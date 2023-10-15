pipeline {
     environment {
       IMAGE_NAME = "alpinehelloworld"
       IMAGE_TAG = "latest"
       STAGING = "eazytraining-staging"
       PRODUCTION = "eazytraining-production"
     }
     agent none
     stages {
         stage('Build image') {
             agent any
             steps {
                script {
                  sh 'docker build -t eazytraining/$IMAGE_NAME:$IMAGE_TAG .'
                }
             }
        }
        stage('Run container based on builded image') {
            agent any
            steps {
               script {
                 sh '''
                    docker run --name $IMAGE_NAME -d -p 80:5000 -e PORT=5000 eazytraining/$IMAGE_NAME:$IMAGE_TAG
                    sleep 5
                 '''
               }
            }
       }
       stage('Test image') {
           agent any
           steps {
              script {
                sh '''
                    curl http://172.17.0.1 | grep -q "Hello world!"
                '''
              }
           }
      }
      stage('Clean Container') {
          agent any
          steps {
             script {
               sh '''
                 docker stop $IMAGE_NAME
                 docker rm $IMAGE_NAME
               '''
             }
          }
     }
     stage('Deploy') {
           agent any
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: '13.38.120.217', keyFileVariable: 'UBUNTU')]) {
                        // Vous pouvez maintenant utiliser UBUNTU dans vos commandes SSH.
                        sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-249-222.eu-west-3.compute.amazonaws.com 'docker run --name myapp -d -p 8084:5000 -e PORT=5000 eazytraining/$IMAGE_NAME:$IMAGE_TAG'"""
                         sh """ssh -o StrictHostKeyChecking=no -i \${UBUNTU} ubuntu@ec2-13-38-249-222.eu-west-3.compute.amazonaws.com 'docker ps'"""
                    }
                }
            }
        }
  }
     post {
       success {
         slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
         }
      failure {
            slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
          }   
    }
}
