

pipeline {
    /* declaritive pipeline */
    agent any

    stages {
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Maven clean / package successful.  Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging') {
            /* agent section can go here as well */
            steps {

            }
        }
    }
}