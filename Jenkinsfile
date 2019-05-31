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
        sh "aws s3 cp example.zip s3://briantoalbucket1"
      }
    }
    
        stage('run CloudFormation template') {
      steps {
        sh "aws cloudformation create-stack --stack-name aws-cloud9-BrianToalCloud9Env-2b3da52fd7be4c80b7812a0aed1414d5 --region us-east-1 --template-body BTCloudFormation.template"
      }
    }

}
}