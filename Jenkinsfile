pipeline {
    agent any
    environment {
        GITNAME = 'ksh0811'
        GITEMAIL = 'iwcksh@gmail.com'
        GITWEBADD = 'https://github.com/ksh0811/fast-code.git'
        GITSSHADD = 'git@github.com:ksh0811/deployment.git'
        GITCREDENTIAL = 'git_cre'
        DOCKERHUB = 'ksh0811/fast'
        DOCKERHUBCREDENTIAL = 'docker_cre'
    }
    stages {
        stage('Checkout Github') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])

            }
            post {
                failure {
                    sh "echo clone failed"
                }
                success {
                    sh "echo clone success"
                }
            }
        }

    }
}