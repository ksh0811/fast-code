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

    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])

    sh "docker build -t ${DOCKERHUB}:${currentBuild.number} ."
                sh "docker build -t ${DOCKERHUB}:latest ."
                // currentBuild.number 젠킨스가 제공하는 빌드넘버 변수
                // oolralra/fast:<빌드넘버> 와 같은 이미지가 만들어질 예정.

    withDockerRegistry(credentialsId: DOCKERHUBCREDENTIAL, url: '') {
        sh "docker push ${DOCKERHUB}:${currentBuild.number}"
        sh "docker push ${DOCKERHUB}:latest"
        }


}

