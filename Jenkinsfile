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
             emailext body: 'Check console output at $BUILD_URL to view the results.#$BUILD_NUMBER'+'/n'+
             +'PROJECT_NAME : #$PROJECT_NAME'+'/n'+
             +'Detail : Project Name' +'/n'+
             +'BUILD_NUMBER : #$BUILD_NUMBER'+'/n'+
             +'Detail : The current build number'+'/n'+
             +'BRANCH_NAME : #$BRANCH_NAME'+'/n'+ 
             +'Detail : For a multibranch project, this will be set to the name of the branch being built, for example in case you wish to deploy to production from master but not from feature branches; if corresponding to some kind of change request, the name is generally arbitrary (refer to CHANGE_ID and CHANGE_TARGET).'+'/n'+
             +'CHANGE_ID : #$CHANGE_ID'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the change ID, such as a pull request number, if supported; else unset.'+'/n'+
             +'CHANGE_URL : #$CHANGE_URL'+'/n'+
             +'Detali : For a multibranch project corresponding to some kind of change request, this will be set to the change URL, if supported; else unset.'+'/n'+
             +'CHANGE_TITLE : #$CHANGE_TITLE'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the title of the change, if supported; else unset.'+'/n'+
             +'CHANGE_AUTHOR : #$CHANGE_AUTHOR'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the username of the author of the proposed change, if supported; else unset.'+'/n'+
             +'CHANGE_AUTHOR_DISPLAY_NAME : #$CHANGE_AUTHOR_DISPLAY_NAME'+'/n'+
             +'Detail :For a multibranch project corresponding to some kind of change request, this will be set to the human name of the author, if supported; else unset.'+'/n'+
             +'CHANGE_AUTHOR_EMAIL : #$CHANGE_AUTHOR_EMAIL'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the email address of the author, if supported; else unset.'+'/n'+
             +'CHANGE_TARGET : #$CHANGE_TARGET'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the target or base branch to which the change could be merged, if supported; else unset.'+'/n'+
             +'CHANGE_BRANCH : #$CHANGE_BRANCH'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the name of the actual head on the source control system which may or may not be different from BRANCH_NAME. For example in GitHub or Bitbucket this would have the name of the origin branch whereas BRANCH_NAME would be something like PR-24.'+'/n'+
             +'CHANGE_FORK : #$CHANGE_FORK'+'/n'+
             +'Detail : For a multibranch project corresponding to some kind of change request, this will be set to the name of the forked repo if the change originates from one; else unset.'+'/n'+
             +'BUILD_ID : #$BUILD_ID'+'/n'+
             +'The current build ID, identical to BUILD_NUMBER for builds created in 1.597+, but a YYYY-MM-DD_hh-mm-ss timestamp for older builds',

             
//            BUILD_DISPLAY_NAME
// The display name of the current build, which is something like "#153" by default.
// JOB_NAME
// Name of the project of this build, such as "foo" or "foo/bar".
// JOB_BASE_NAME
// Short Name of the project of this build stripping off folder paths, such as "foo" for "bar/foo".
// BUILD_TAG
// String of "jenkins-${JOB_NAME}-${BUILD_NUMBER}". All forward slashes ("/") in the JOB_NAME are replaced with dashes ("-"). Convenient to put into a resource file, a jar file, etc for easier identification.
// EXECUTOR_NUMBER
// The unique number that identifies the current executor (among executors of the same machine) that’s carrying out this build. This is the number you see in the "build executor status", except that the number starts from 0, not 1.
// NODE_NAME
// Name of the agent if the build is on an agent, or "master" if run on master
// NODE_LABELS
// Whitespace-separated list of labels that the node is assigned.
// WORKSPACE
// The absolute path of the directory assigned to the build as a workspace.
// JENKINS_HOME
// The absolute path of the directory assigned on the master node for Jenkins to store data.
// JENKINS_URL
// Full URL of Jenkins, like http://server:port/jenkins/ (note: only available if Jenkins URL set in system configuration)
// BUILD_URL
// Full URL of this build, like http://server:port/jenkins/job/foo/15/ (Jenkins URL must be set)
// JOB_URL
// Full URL of this job, like http://server:port/jenkins/job/foo/ (Jenkins URL must be set)
// GIT_COMMIT
// The commit hash being checked out.
// GIT_PREVIOUS_COMMIT
// The hash of the commit last built on this branch, if any.
// GIT_PREVIOUS_SUCCESSFUL_COMMIT
// The hash of the commit last successfully built on this branch, if any.
// GIT_BRANCH
// The remote branch name, if any.
// GIT_LOCAL_BRANCH
// The local branch name being checked out, if applicable.
// GIT_CHECKOUT_DIR
// The directory that the repository will be checked out to. This contains the value set in Checkout to a sub-directory, if used.
// GIT_URL
// The remote URL. If there are multiple, will be GIT_URL_1, GIT_URL_2, etc.
// GIT_COMMITTER_NAME
// The configured Git committer name, if any, that will be used for FUTURE commits from the current workspace. It is read from the Global Config user.name Value field of the Jenkins Configure System page.
// GIT_AUTHOR_NAME
// The configured Git author name, if any, that will be used for FUTURE commits from the current workspace. It is read from the Global Config user.name Value field of the Jenkins Configure System page.
// GIT_COMMITTER_EMAIL
// The configured Git committer email, if any, that will be used for FUTURE commits from the current workspace. It is read from the Global Config user.email Value field of the Jenkins Configure System page.
// GIT_AUTHOR_EMAIL
// The configured Git author email, if any, that will be used for FUTURE commits from the current workspace. It is read from the Global Config user.email Value field of the Jenkins Configure System page.

                    to: "vahid.h63@gmail.com", 
                    subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER'
         }  
         success {  
             echo 'This will run only if successful'  
            // emailext body: 'Check console output at $BUILD_URL to view the results.#$BUILD_NUMBER', 
            //         to: "vahid.h63@gmail.com", 
            //         subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER'
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