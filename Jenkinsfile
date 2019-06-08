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
    }
}
