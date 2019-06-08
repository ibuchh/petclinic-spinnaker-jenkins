pipeline {
    agent any
 
    stages {
        stage('Maven Install') {
           agent {
              docker {
                 image 'maven:3.5.0'
              }
          }
        steps {
        sh 'mvn package -DskipTests'
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
