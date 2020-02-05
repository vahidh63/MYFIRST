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
             emailext body: 'Check console output at $BUILD_URL to view the results.$BUILD_NUMBER'
             +'PROJECT_NAME : $PROJECT_NAME /n'
             +'Detail : Project Name /n'
             +'BUILD_NUMBER : $BUILD_NUMBER /n'
             +'Detail : The current build number/n',
            to: "vahid.h63@gmail.com", 
            subject: 'Jenkins build is back to normal: $PROJECT_NAME - $BUILD_NUMBER'
         }  
         success {  
             echo 'This will run only if successful'  `
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