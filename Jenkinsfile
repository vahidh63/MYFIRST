def MESSAGE_DETAILS = "BUILD DETAILS:  - ${BUILD_URL} "+
"Project name : ${env.PROJECT_NAME} \n"+
"Job Name : ${env.JOB_NAME} \n"+
"Build Number : #${env.BUILD_NUMBER} "

pipeline {  
     agent any  
     stages {  
         stage('Test') {  
             steps {  
                 sh 'echo "test run!"; '  
             }  
         }  
     }  
     post {  
         always {  
             echo 'This will always run'  
              emailext attachLog: false, body: "Build Finished Successfully.<br></br>" + MESSAGE_DETAILS, mimeType: 'text/html', subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - SUCCESS", to: "vahid.h63@gmail.com"
              office365ConnectorSend color: '05b222', status: 'SUCCESS', webhookUrl: '${TEAM_WEBHOOK}'
             emailext body: MESSAGE_DETAILS,
            to: "vahid.h63@gmail.com", 
            subject: 'Jenkins build : $PROJECT_NAME - $BUILD_NUMBER'
         }  
         success {  
             echo 'This will run only if successful'
         }  
         failure {  
             mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "vahid.h63@gmail.com";  
         }  
         unstable {  
             echo 'This will run only if the run was marked as unstable'  
         }  
         changed {  
             echo 'This will run only if the state of the Pipeline has changed'  
             echo 'For example, if the Pipeline was previously failing but is now successful'  
         }  
     }  
 }