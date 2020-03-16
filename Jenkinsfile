pipeline {
    agent any
    stages {
    
    stage('Build Application') {
            steps {
                sh 'gradle clean build'
            }
            post {
                success { 
                    echo "Now Archiving the Artificates"
                    archiveArtificats artifacts: 'build/libs/*.war'
                }        
            }
        }
        
        stage('Create Docker image') {
            steps {
                sh  "docker build . -t tomcatdemoweb:${env.BUILD_ID}
            }
        }
    }
}
