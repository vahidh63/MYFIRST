pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                ansiColor('xterm') {
                echo 'something that outputs ansi colored stuff'
                }
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
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