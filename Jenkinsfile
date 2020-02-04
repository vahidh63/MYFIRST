pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
                    sh 'something that outputs ansi colored stuff'
                }
                ansiColor('xterm') {
                echo 'something that outputs ansi colored stuff'
                }
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
                echo 'Deploying....'
            }
        }
    }
}