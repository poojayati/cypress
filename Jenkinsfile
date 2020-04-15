#!/usr/bin/env groovy 

 
pipeline{
  agent any

        environment {
        EMAIL_TO = 'poojayati7@gmail.com'
                   }
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
                script{
                      try{
                        nodejs(nodeJSInstallationName:'nodejs'){
                        
                        sh 'npm run multi-report'
                        currentBuild.result='SUCCESS'
                        } 
                        }catch(err){
                        currentBuild.result='FAILURE'

                        }

                }
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

             post{
       /* // triggered when buildResult status is SUCCESS
        success {
            slackSend (
                    color: '#8F1FE1',
                    iconEmoji: ':smiley:',
                    channel: '#coalition-tribe-qe-pipeline',
                    message: "The pipeline ${currentBuild.fullDisplayName} has completed :recycle:. SIT Html Report is here (<https://test-reports.qantasloyalty.io/${APP_TYPE}/${reportTimeStamp}/SIT/TestReports.html|Open Report>)"
            )
        }
        // triggered when buildResult is FAILURE
        failure {
            slackSend (
                    color: 'danger',
                    iconEmoji: ':neutral_face:',
                    channel: '#coalition-tribe-qe-pipeline',
                    message: "Oh no! Build failed :neutral_face: - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>). SIT Html Report is here (<https://test-reports.qantasloyalty.io/${APP_TYPE}/${reportTimeStamp}/SIT/TestReports.html|Open Report>)"
            )
        }
        // triggered when buildResult is UNSTABLE
        unstable {
            slackSend (
                    color: 'warning',
                    iconEmoji: ':cold_sweat:',
                    channel: '#coalition-tribe-qe-pipeline',
                    message: "Build unstable :cold_sweat: - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>). SIT Html Report is here (<https://test-reports.qantasloyalty.io/${APP_TYPE}/${reportTimeStamp}/SIT/TestReports.html|Open Report>)"
            )
        }*/

        //EMAIL notification code
        success{

          //script{
          //set variables
         /* def subject = "${env.JOB_NAME} - Build #${env.BUILD_NUMBER} ${currentBuild.result}"
          def content = "${JELLY_SCRIPT,template='html'}"

          //send email
          emailext(body:content,mimeType:'text/html',replyTo='$DEFAULT_REPLYTO',subject=subject,
          to:'poojayati7@gmail.com',attachLog:true)*/

          emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
                    to: "${EMAIL_TO}", 
                    subject: 'Build failed in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'



         // }

          }
        }
      }
  }
}





