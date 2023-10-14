pipeline {
agent any
stages {
stage('Deploy') {
steps {
// Créer une tâche CodeDeploy
withAWSCodeDeploy(profileName: 'default') {
deploy(applicationName: 'mon-application',  imageName: 'mrad90/alpinehelloworld')
}
}
}
}
}
