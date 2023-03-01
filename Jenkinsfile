pipeline {
    agent {
        docker {
            image '158.160.25.103:8083/build-cont'
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('copy project from github') {
            steps {
                git 'https://github.com/elmcslay/DO_edu-HW11_1.git'
            }
        }

        stage('build project') {
            steps {
                sh 'mvn package'
            }
        }

        stage('create docker image') {
            steps {
                sh 'docker build --no-cache -t dep -f Dockerfile target/'
                sh 'docker tag dep 158.160.25.103:8083/dep && docker push 158.160.25.103:8083/dep'
            }
        }

        stage('add&run container to demo-deploy') {
            steps {
                //sh 'ssh-keyscan -H 51.250.102.45 >> ~/.ssh/known_hosts'
                sh '''ssh root@51.250.102.45 << EOF
                        sudo uname -n
                    EOF'''
                //sh 'docker pull 158.160.25.103:8083/dep'
                //sh 'docker run -it -p 8080:8080 158.160.25.103:8083/dep'  
            }
        }
    }
}