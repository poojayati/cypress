pipeline{
  agent any
        stages{
            stage('checkout'){
              steps{
                checkout scm
              }
            }

            stage('build'){
               steps{
                //nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm install'

               //}
              }
            }

            stage('test step'){

              steps{
                //nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm run headedTest'

                //}
              }
            }
  }
}





