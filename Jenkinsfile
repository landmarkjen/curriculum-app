pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/landmarkjen/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      parallel {
        stage('Log') {
          steps {
            sh 'ls -la'
          }
        }

        stage('error') {
          steps {
            sh 'ls -la'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile -t fuze365/curriculum-front:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'Jenniferada'
        DOCKERHUB_PASSWORD = 'Tasontasie33@'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push fuze365/curriculum-front:latest'
      }
    }

  }
}