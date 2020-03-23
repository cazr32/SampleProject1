pipeline{
    agent any
    stages{
        stage('Build Application'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts..."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        /*stage('Deploy in Staging Environment'){
            steps{
                sh 'docker build . -t tomcatsamplewebapp:${env.BUILD_ID}'
            }          
        }*/
        stage('Create Tomcat Docker Image'){
            steps{
                sh 'docker build . -t tomcatsamplewebapp:${env.BUILD_ID}'
            }          
        }
    }
}