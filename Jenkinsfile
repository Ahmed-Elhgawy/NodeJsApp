pipeline {
    agent {label "kubeagant"}

    stages{

       stage('make docker image') {
            steps {
                sh "docker build . -t node:app"
                sh "docker tag node:app elhgawy/node:app"
                withCredentials([usernamePassword(credentialsId: 'Docker', passwordVariable: 'PASSWD', usernameVariable: 'USER')]) {
                    sh "docker login -u $USER -p $PASSWD"
                }
                sh "docker push elhgawy/node:app"                
            }
        }

        stage('app provisionning') {
            steps {
                sh "kubectl apply -f deployment/deployment.yaml"
                sh "kubectl apply -f deployment/service.yaml"
            }
        }
        
    }

    post {

        success {
            slackSend color: 'good', message: 'App deployed to cluster successfully', tokenCredentialId: 'Slack'
        }

        failure {
            slackSend color: 'danger', message: 'App failed to be deployed to cluster', tokenCredentialId: 'Slack'
        }
    }
    
}
