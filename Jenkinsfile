pipeline{
    agent any
    tools{
        maven 'Maven3'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'c5dd6ce3-8d74-461f-be1b-3e2afe372e98', path: '', url: 'http://localhost:1010/')], contextPath: null, war: '**/target/*.war'
            }
        }
    }
}
