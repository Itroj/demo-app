pipeline {
    agent any 

    stages {
        stage('checkout') {
            steps {
            echo 'kod zostal pobrany z repozytorium'
            }
        }

        stage('build') {
            steps {
                sh 'mkdir -p build'
                sh 'echo "Hello from demo app" > build/app.txt'
            }
        }

        stage('test') {
            steps  {
                sh 'test -f build/app.txt'
                sh 'grep "Hello" build/app.txt'
            }
        }

        stage('package') {
            steps {
                sh 'tar -czf app.tar.gz build/'
            }
        }
    }

    post {
        success {
            echo 'Build, test i package zakonczone sukcesem'
        }

        failure {
            echo 'cos poszlo nie tak'
        }
    }
}