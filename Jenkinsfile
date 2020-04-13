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
                nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm install'

               }
              }
            }

            stage('test'){

              steps{
                nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm run multi-report'

                }
              }
            }

             stage('generate reports'){

              steps{
                nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm run generate-reports'

                }
              }
            }
            
  }
}





