pipeline {
    agent any

    environment {
        REGISTRY_IP = credentials('registry-ip')
        REGISTRY_PORT = credentials('registry-port')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Code source récupéré depuis GitHub'
            }
        }

        stage('Build calc-service') {
            steps {
                dir('calc-service') {
                    sh 'docker build -t $REGISTRY_IP:$REGISTRY_PORT/calculator-calc:latest .'
                }
            }
        }

        stage('Build sum-service') {
            steps {
                dir('sum-service') {
                    sh 'docker build -t $REGISTRY_IP:$REGISTRY_PORT/calculator-sum:latest .'
                }
            }
        }

        stage('Build sub-service') {
            steps {
                dir('sub-service') {
                    sh 'docker build -t $REGISTRY_IP:$REGISTRY_PORT/calculator-sub:latest .'
                }
            }
        }

        stage('Build mul-service') {
            steps {
                dir('mul-service') {
                    sh 'docker build -t $REGISTRY_IP:$REGISTRY_PORT/calculator-mul:latest .'
                }
            }
        }

        stage('Build div-service') {
            steps {
                dir('div-service') {
                    sh 'docker build -t $REGISTRY_IP:$REGISTRY_PORT/calculator-div:latest .'
                }
            }
        }
    }

    post {
        success {
            echo 'CI : toutes les images ont été construites avec succès !'
        }
        failure {
            echo 'CI : échec du pipeline.'
        }
    }
}
