#!groovy

pipeline {
  agent none
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
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t ibuchh/spring-petclinic:latest .'
      }
    }
  }
}
