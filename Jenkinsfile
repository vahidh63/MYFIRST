pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                 timeout(45) {
                wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
                    sh 'something that outputs ansi colored stuff'
                }
            }
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