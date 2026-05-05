pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Wybierz srodowisko')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'czy uruchomic testy?')
    }

    stages {
        stage('info') {
            steps {
                echo "srodowisko: ${params.ENVIRONMENT}"
                echo "uruchomic testy: ${params.RUN_TESTS}"
            }
        }

        stage('build') {
            steps {
                sh 'echo "building..."'
            }
        }

        stage('Test') {
            steps {
                when {
                    expression {
                        return params.RUN_TESTS
                    }
                }
                steps {
                    sh 'echo "testing..."'
                }
            }
        }

        stage('deploy') {
            steps {
                echo "deploy na srodowisko: ${params.ENVIRONMENT}"
            }
        }
    }
}