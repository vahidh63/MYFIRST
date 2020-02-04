pipeline {
    agent any
    // wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
    //                 sh 'something that outputs ansi colored stuff'
    //             }
    stages {
        stage('Build') {
            steps {
                
                
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                ansiColor('xterm') {
                    echo "TERM=${env.TERM}"
                    // prints out TERM=xterm
                }
                echo 'Testing..'
                echo 'Testinglllllllllll..'
            }
        }
        stage('Deploy') {
            steps {
                ansiColor('xterm') {
                echo 'something that outputs ansi colored stuff'
                }
                echo 'Deploying....'
            }
        }
    }
}