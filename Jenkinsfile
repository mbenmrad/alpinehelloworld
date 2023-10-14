pipeline {
agent any
stages {
stage('Deploy') {
steps {
// Créer une tâche CodeDeploy
echo "HEllo"
sh 'docker ps -a'
  withAWSCodeDeploy(profileName: 'default') {
    echo "HEllo2"
  sh 'docker ps -a'
}
}
}
}
}
