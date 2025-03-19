pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/devasriashok/jenkins.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t devasria/mysimplewebapplication .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push devasria/mysimplewebapplication'
               }
            }
            }
}
}
