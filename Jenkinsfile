pipeline {
    agent any
    stages {
        
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    app = docker.build("demo")
                    
                }
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    docker.withRegistry('294025978207.dkr.ecr.us-east-1.amazonaws.com/demo', 'demo-ecr-credentials') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
       
        } 
    }
}
