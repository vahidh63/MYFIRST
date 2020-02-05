def MESSAGE_DETAILS = "BUILD DETAILS:  - ${BUILD_URL} <br></br>\n"+
"Project name : ${env.PROJECT_NAME} <br></br>\n"+
"Job Name : ${env.JOB_NAME} <br></br>\n"+
"Build Number : ${env.BUILD_NUMBER} <br></br>\n" + 
"CHANGE_ID : ${env.CHANGE_ID} <br></br>\n" + 
"BRANCH_NAME : ${env.BRANCH_NAME} <br></br>\n" + 
"CHANGE_URL : ${env.CHANGE_URL} <br></br>\n" + 
"CHANGE_AUTHOR : ${env.CHANGE_AUTHOR} <br></br>\n" + 
"CHANGE_AUTHOR_DISPLAY_NAME : ${env.CHANGE_AUTHOR_DISPLAY_NAME} <br></br>\n" + 
"CHANGE_AUTHOR_EMAIL : ${env.CHANGE_AUTHOR_EMAIL} <br></br>\n" + 
"CHANGE_TARGET : ${env.CHANGE_TARGET} <br></br>\n" + 
"CHANGE_BRANCH : ${env.CHANGE_BRANCH} <br></br>\n" + 
"CHANGE_FORK : ${env.CHANGE_FORK} <br></br>\n" + 
"BUILD_ID : ${env.BUILD_ID} <br></br>\n" + 
"BUILD_DISPLAY_NAME : ${env.BUILD_DISPLAY_NAME} <br></br>\n" + 
"JOB_BASE_NAME : ${env.JOB_BASE_NAME} <br></br>\n" + 
"BUILD_TAG : ${env.BUILD_TAG} <br></br>\n" + 
"EXECUTOR_NUMBER : ${env.EXECUTOR_NUMBER} <br></br>\n" + 
"NODE_NAME : ${env.NODE_NAME} <br></br>\n" + 
"NODE_LABELS : ${env.NODE_LABELS} <br></br>\n" + 
"WORKSPACE : ${env.WORKSPACE} <br></br>\n" + 
"JENKINS_HOME : ${env.JENKINS_HOME} <br></br>\n" + 
"JENKINS_URL : ${env.JENKINS_URL} <br></br>\n" + 
"GIT_COMMIT : ${env.GIT_COMMIT} <br></br>\n" + 
"GIT_PREVIOUS_COMMIT : ${env.GIT_PREVIOUS_COMMIT} <br></br>\n" + 
"GIT_PREVIOUS_SUCCESSFUL_COMMIT : ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT} <br></br>\n" + 
"GIT_BRANCH : ${env.GIT_BRANCH} \n" + 
"GIT_LOCAL_BRANCH : ${env.GIT_LOCAL_BRANCH} <br></br>\n" + 
"GIT_CHECKOUT_DIR : ${env.GIT_CHECKOUT_DIR} <br></br>\n" + 
"GIT_COMMITTER_NAME : ${env.GIT_COMMITTER_NAME} <br></br>\n" + 
"GIT_COMMITTER_EMAIL : ${env.GIT_COMMITTER_EMAIL} <br></br>\n" + 
"GIT_AUTHOR_NAME : ${env.GIT_AUTHOR_NAME} <br></br>\n" + 
"GIT_AUTHOR_EMAIL : ${env.GIT_AUTHOR_EMAIL} <br></br>\n" + 
"GIT_URL : ${env.GIT_URL} <br></br>\n"

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
           // emailext attachLog: false, body: "Build Finished Successfully.<br></br>" + MESSAGE_DETAILS, mimeType: 'text/html', subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - SUCCESS", to: "vahid.h63@gmail.com"
           // emailext body: MESSAGE_DETAILS,to: "vahid.h63@gmail.com", subject: 'Jenkins build : $PROJECT_NAME - $BUILD_NUMBER'
         }  
         success {  
            echo 'This will run only if successful'
            emailext attachLog: false, body: "Build Finished Successfully.<br></br>" + MESSAGE_DETAILS, mimeType: 'text/html', subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - SUCCESS", 
            to: "vahid.h63@gmail.com,prasath.sivasubramaniyan@dxc.com"

         }  
         failure {  
            emailext attachLog: false, body: "Build Finished Fail.<br></br>" + MESSAGE_DETAILS, mimeType: 'text/html', subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - SUCCESS", 
            to: "vahid.h63@gmail.com,prasath.sivasubramaniyan@dxc.com"

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