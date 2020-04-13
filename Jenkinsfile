pipeline{
  agent any
        stages{
            stage('checkout'){
              steps{
                checkout scm
              }
            }

            stage('clean'){
               steps{
                nodejs(nodeJSInstallationName:'nodejs'){
                
                sh 'npm run clean-reports'

               }
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

             stage('publish reports'){
               steps{
                nodejs(nodeJSInstallationName:'nodejs'){
                
                  sh 'npm run generate-reports'
                  publishHTML(target: [
                  reportDir            : 'mochawesome-report',
                  reportFiles          : 'finalReport.html',
                  reportName           : "Mocha Test Report",
                  keepAll              : false,
                  alwaysLinkToLastBuild: true,
                  allowMissing         : false
                ])

                }
              }
            }
  }
}





