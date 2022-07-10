pipeline {
    agent any

    stages{
        stage('Fetch code') {
          steps{
              git branch: 'v1', credentialsId: 'cd5b3433-f2e9-44fc-a55d-41595cfccc56', url:'https://github.com/anup5/vprofile-repo.git'
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
