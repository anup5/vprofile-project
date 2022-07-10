pipeline {
    agent any

    stages{
        stage('Fetch code') {
          steps{
              git branch: 'v1', credentialsId: 'github', url:'https://github.com/anup5/vprofile-repo.git'
          }  
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
            }

        }

    }
}
