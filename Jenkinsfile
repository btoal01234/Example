#!/usr/bin/env groovy
pipeline {
  agent any
  options { skipDefaultCheckout()
            disableConcurrentBuilds()
          }

  stages {
    stage('Build Dependencies') {
      steps {
        checkout scm
        sh "npm install"
      }
    }




     stage('Package') {

      steps {
        sh  "npm run build-aws-resource"
      }
    }
    
    stage('S3 upload') {
      steps {
        sh "aws s3 cp Example.zip s3://briantoalbucket1"
      }
    }

}
}