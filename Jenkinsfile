pipeline {
    agent any
  
    stages {
 stage('Pull Repository') {
            steps {
                // Pull the repository source code from Git
                git branch: 'master', url: 'https://github.com/MedBouhdida1/jenkins.git'
            }
        }
    
        stage('Build Spring') {
            
            steps {
                sh "mvn clean install"

            }
        }
        stage('Build docker image') {
            steps {
             script{
                sh 'sudo docker build -t firstspring .'
             }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:8080 firstspring'
                }
            }
        }
    }
}
