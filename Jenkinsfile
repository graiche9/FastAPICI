pipeline{
    agent {
        docker {
            image "postman/newman"
            args "--entrypoint=''"
        }
        
    }
     triggers { upstream(upstreamProjects: 'TEST', threshold: hudson.model.Result.SUCCESS) }

    stages{
        stage('verifier la version de newman'){
            steps{
                sh 'newman --version'
            }
        }
        stage('Test API'){
            steps{
                sh 'newman run collections/Testhelloworld.postman_collection.json'
            }
        }
    }
    post{
        always {
            junit 'newman-report.xml'
        }
    }
}