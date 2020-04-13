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

             stage('generate reports'){
               steps{
                nodejs(nodeJSInstallationName:'nodejs'){
                
                  sh 'npm run generate-reports'
                 

                }
              }
            }

            stage('publish reports'){
              steps{
                 publishHTML(target: [
                  reportDir            : 'mochawesome-report',
                  reportFiles          : 'finalReport.html',
                  reportName           : 'MochaTestReport',
                  keepAll              : false,
                  alwaysLinkToLastBuild: true,
                  allowMissing         : false
                ])
              }
            }
  }
}





