pipeline{
  //agent { label 'nodejs8' }
    agent any
    environment {
        scannerHome = tool 'SonarQubeScanner'
    }
  stages{
    stage ('checkout'){
      steps{
        checkout scm
      }
    }
    // stage ('install modules'){
    //   steps{
    //     sh '''
    //       npm install --verbose -d 
    //       npm install --save classlist.js
    //     '''
    //   }
    // }
    // stage ('test'){
    //   steps{
    //     sh '''
    //       $(npm bin)/ng test --watch=false --browsers Chrome_no_sandbox
    //     '''
    //   }
    //   post {
    //       always {
    //         junit "test-results.xml"
    //       }
    //   }
    // }
    stage ('code quality'){
      steps{
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/sonar-scanner"
        }
      }
    }
    // stage ('code quality'){
    //   steps{
    //     sh '$(npm bin)/ng lint'
    //   }
    // }

  }
}
