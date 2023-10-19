pipeline{
    agent any
    stages{
        stage('Delete existing docker image and container'){
            steps{
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/herambh17/website']])
            script{
            bat 'docker rmi -f herambh17/website'
            bat 'docker rm -f cont_html'
            }
            }
        }
        stage('Build Docker image'){
            steps{
            script{
            bat 'docker build -t herambh17/website .'
            }
            }
        }
        stage('Push image to Docker Hub'){
            steps{
            script{
            bat 'docker login -u "herambhkumawat17" -p "Herkum@17" docker.io'
            bat 'docker push herambh17/website:latest'
            }
            }
        }
        stage('Creating new Container'){
            steps{
                script{
                    bat 'docker run -it -d -P --name=cont_html herambh17/website'
            }
        }
    }
}
}
