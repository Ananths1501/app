pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/Ananths1501/app.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean'  
                sh 'mvn install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ananth1501/simpleapplication .'  
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                    sh 'docker push ananth1501/simpleapplication'
                }
            }
        }
    }
}

