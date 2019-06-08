pipeline {
    agent any
    tools {
        maven 'M3'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn package -DskipTests=true' 
            }
        }
         stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    app = docker.build("ibuchh/petclinic-spinnaker-jenkins")
                }
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_ibuchh') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
    }
}
