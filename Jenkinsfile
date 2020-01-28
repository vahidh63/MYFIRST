pipeline {
    agent { label 'market-dev'}
    environment {
        APPNAME             = "mytest"
    }

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {   

        stage ("Publishing image")  {
		    steps{
                script {

                    echo "Docker image build ${MGTACRDEV}/$APPNAME:1.0.0"
                       
                        }

                }
            }
      } 
        
 

        stage ("Deploy to Prod")  {
	    agent {
                 docker {
                     image 'microsoft/azure-cli'
                     args '-u root:root'
                     reuseNode true
                 }
             }
            when { branch 'master'}
            steps{
                script {
                        echo "Preparing deployment of 1.0.0 in namespace: $DEV"
                         echo "deploying microservices"
                            
                            }
                        currentBuild.description = "Release Version-Dev: 1.0.0"
                         
                }
            }
        }
      
	stage ("Deploy to Prod-DR")  {
	    agent {
                 docker {
                     image 'microsoft/azure-cli'
                     args '-u root:root'
                     reuseNode true
                 }
             }
            when { branch 'master'}
            steps{
                script {
                        echo "Preparing deployment of 1.0.0 in namespace: $DEV"
                     }
                        currentBuild.description = "Release Version-Dev: 1.0.0"
                         
                }
            }
        }
	    
	    
	    
    } //stages

    post {
        always {
            echo 'One way or another, I have finished'
            cleanWs() /* clean up our workspace */
        }
        success {
           echo 'I succeeded!'
           office365ConnectorSend color: '05b222', status: 'SUCCESS', webhookUrl: '${TEAM_WEBHOOK}'
        }
        unstable {
            echo 'I am unstable :/'
        }
        
        failure {
            echo 'I failed :('
            office365ConnectorSend color: 'd00000', status: 'FAILURE', webhookUrl: '${TEAM_WEBHOOK}'
        }
        
        changed {
            echo 'Things were different before...'
        } 
    }  
}//pipeline ends
