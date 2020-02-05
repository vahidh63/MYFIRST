def MESSAGE_DETAILS = "BUILD DETAILS:  - ${BUILD_URL} \n"+
"Project name : ${env.PROJECT_NAME} \n"+
"Job Name : ${env.JOB_NAME} \n"+
"Build Number : ${env.BUILD_NUMBER} \n" + 
"CHANGE_ID : ${env.CHANGE_ID} \n" + 
"BRANCH_NAME : ${env.BRANCH_NAME} \n" + 
"CHANGE_URL : ${env.CHANGE_URL} \n" + 
"CHANGE_AUTHOR : ${env.CHANGE_AUTHOR} \n" + 
"CHANGE_AUTHOR_DISPLAY_NAME : ${env.CHANGE_AUTHOR_DISPLAY_NAME} \n" + 
"CHANGE_AUTHOR_EMAIL : ${env.CHANGE_AUTHOR_EMAIL} \n" + 
"CHANGE_TARGET : ${env.CHANGE_TARGET} \n" + 
"CHANGE_BRANCH : ${env.CHANGE_BRANCH} \n" + 
"CHANGE_FORK : ${env.CHANGE_FORK} \n" + 
"BUILD_ID : ${env.BUILD_ID} \n" + 
"BUILD_DISPLAY_NAME : ${env.BUILD_DISPLAY_NAME} \n" + 
"JOB_BASE_NAME : ${env.JOB_BASE_NAME} \n" + 
"BUILD_TAG : ${env.BUILD_TAG} \n" + 
"EXECUTOR_NUMBER : ${env.EXECUTOR_NUMBER} \n" + 
"NODE_NAME : ${env.NODE_NAME} \n" + 
"NODE_LABELS : ${env.NODE_LABELS} \n" + 
"WORKSPACE : ${env.WORKSPACE} \n" + 
"JENKINS_HOME : ${env.JENKINS_HOME} \n" + 
"JENKINS_URL : ${env.JENKINS_URL} \n" + 
"GIT_COMMIT : ${env.GIT_COMMIT} \n" + 
"GIT_PREVIOUS_COMMIT : ${env.GIT_PREVIOUS_COMMIT} \n" + 
"GIT_PREVIOUS_SUCCESSFUL_COMMIT : ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT} \n" + 
"GIT_BRANCH : ${env.GIT_BRANCH} \n" + 
"GIT_LOCAL_BRANCH : ${env.GIT_LOCAL_BRANCH} \n" + 
"GIT_CHECKOUT_DIR : ${env.GIT_CHECKOUT_DIR} \n" + 
"GIT_COMMITTER_NAME : ${env.GIT_COMMITTER_NAME} \n" + 
"GIT_COMMITTER_EMAIL : ${env.GIT_COMMITTER_EMAIL} \n" + 
"GIT_AUTHOR_NAME : ${env.GIT_AUTHOR_NAME} \n" + 
"GIT_AUTHOR_EMAIL : ${env.GIT_AUTHOR_EMAIL} \n" + 
"GIT_URL : ${env.GIT_URL} \n"

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