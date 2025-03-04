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
                sh 'newman run Testhelloworld.postman_collection.json -r cli,junit --reporter-junit-export="newman-report.xml"'
            }
        }
    }
    post{
        always {
            junit 'newman-report.xml'
        }
    }
}