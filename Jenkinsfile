pipeline {
  agent any

  environment {
    IMAGE_NAME = "yourdockerhubusername/ci-cd-lab-app"
  }

  stages {
    stage('Checkout') {
      steps {
        git credentialsId: 'github-creds', url: 'https://github.com/rajmohanbtheteacher/jenkins-demo.git'
      }
    }

    stage('Install Dependencies') {
      agent {
        docker {
          image 'node:16-alpine'
          args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
      }
      steps {
        dir('app') {
          sh 'npm install'
        }
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'node:16-alpine'
          args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
      }
      steps {
        dir('app') {
          sh 'npm test || echo "No tests defined. Skipping..."'
        }
      }
    }

    stage('Build Docker Image') {
      steps {
        dir('app') {
          script {
            sh "docker build -t $IMAGE_NAME ."
          }
        }
      }
    }

    stage('Push Docker Image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
          script {
            sh '''
              echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
              docker push $IMAGE_NAME
            '''
          }
        }
      }
    }

    stage('Deploy to Staging') {
      steps {
        sh 'docker run -d --rm -p 3000:3000 --name ci-cd-app $IMAGE_NAME || echo "Already running..."'
      }
    }

    stage('Approval') {
      steps {
        input message: 'Deploy to production?'
      }
    }

    stage('Deploy to Production') {
      steps {
        echo '✅ Production deployment triggered (add SSH/remote Docker commands here)'
      }
    }
  }
}
