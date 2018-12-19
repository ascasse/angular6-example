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
    stage ('install modules'){
      steps{
        sh '''
          npm install --verbose -d 
          npm install --save classlist.js
        '''
      }
    }
    //stage ('Unit tests') {
    //  sh "npm test"
    //}
    // stage ('code quality'){
    //   steps{
    //     withSonarQubeEnv('sonarqube') {
    //         sh "${scannerHome}/sonar-scanner"
    //     }
    //   }
    // }
    stage ('code quality'){
      steps{
        sh '$(npm bin)/ng lint'
      }
    }

  }
}
