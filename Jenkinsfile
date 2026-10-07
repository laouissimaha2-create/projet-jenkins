pipeline {
    agent any

    stages {
        stage('run') {
            steps {
                sh 'javac bvs.java'
                sh 'java bvs'
            }
        }

        stage('affichage') {
            steps {
                sh 'echo "Hello BVS"'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
