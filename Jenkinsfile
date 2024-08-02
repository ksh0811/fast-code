pipeline {
    agent any
    environment {
        GITNAME = 'ksh0811'
        GITMAIL = 'iwcksh@gmail.com'
        GITWEBADD = 'https://github.com/ksh0811/fast-code.git'
        GITSSHADD = 'git@github.com:ksh0811/fast-code.git'
        GITCREDENTIAL = 'git_cre'
        DOCKERHUB = 'ksh0811/fast'
        DOCKERHUBCREDENTIAL = 'docker_cre'//
    }
    stages {
        stage('start') {
            steps {
                sh "echo hello jenkins!!!"
            }
            post {
                failure {
                    sh "echo failed"
                }
                success {
                    sh "echo success"
                }
            }
        }
    }

    sh "docker build -t ${DOCKERHUB}:${currentBuild.number} ."
    sh "docker build -t ${DOCKERHUB}:latest ."
}

