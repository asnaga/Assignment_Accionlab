# Assignment_Accionlab
#3 Build a Deployment Pipeline

#Using Jenins Pipeline


pipeline {
      agent any

      environment {
            DOKER_IMAGE = "mydockerhubuser/my-app"
            IMAGE_TAG = "${env.BUILD_NUMBER}"
      }

      stages {
        stage ('Checout Code') {
          steps {
              git branch: 'main', url: 'https://giturl'
          }
      }

      stage ('Build Docker Image') {
        steps {
          scripts {
            sh "docker build -t ${DOKER_IMAGE}:${IMAGE_TAG} ."
            }
        }
      }

      stage ('Run Security Scan')
        steps {
          scripts {
            sh "trivy image --exit-code 1 --severity HIGH,CRITICAL ${DOKER_IMAGE}:${IMAGE_TAG}"
            }
          }
        }
      }

      stage('Deploy to Kubernetes') {
        steps {
          scrpt {
            sh """
              kubectl set image deployment/my-app my-contaner=${DOKER_IMAGE}:${IMAGE_TAG} --record
              kubectl rollout status deployment/my-app
              """
          }
        }
      }
      post {
          failure {
              slacSend(channel: '#deployments', message: "Deployment Fail! Check Logs.", color: 'danger')
    }
    success {
              slacSend(channel: '#deployments', message: "Deployment Successfull! Image: ${DOKER_IMAGE}:${IMAGE_TAG}", color: 'good')
    }
  }
}
