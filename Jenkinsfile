pipeline{
    agent{
        docker {
            image "postman/newman"
            args "--entrypoint=''"
        }
    }
    stages{
         stage('Test API1'){
            steps{
                sh 'newman --version'
            }
        }
        stage('Test API2'){
            steps{
                sh 'newman run collection/collection.json  -r cli,junit --reporter-junit-export="newman-report.xml"'
            }
        }
    }

    post {
        always {
            junit 'newman-report.xml' 
        }


    }
}