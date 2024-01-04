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
                sh "docker push"                
            }
        }

        stage('app provisionning') {
            steps {
                sh "kubectl apply -f deployment/deployment.yml"
                sh "kubectl apply -f deployment/service.yml"
            }
        }
        
    }
    
}
